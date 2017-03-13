# Geneea Syntaxnet docker images

## Building the syntaxnet container

    # build syntaxnet docker image
    cd build && sudo docker build -t geneea-syntaxnet .
    
    # build Czech and Russian-SynTagRus models from Universal Dependencies
    cd build-csru && sudo docker build -t geneea-syntaxnet-csru .

## Running the syntaxnet container

	# run geneea-syntaxnet-csru docker image
	# docker will map /home/share/corpora folder from sandbox (host) to /home/share/corpora in the running container
	sudo docker run -it -v /home/share/corpora:/home/share/corpora geneea-syntaxnet-csru bash

	# parse some text, use language model from 'syntaxnet/models/parsey_universal/Czech'
	echo 'Bob přinesl Alici pizzu.' | syntaxnet/models/parsey_universal/parse.sh syntaxnet/models/parsey_universal/Czech

	# parse 10 lines of bible.txt and show the syntactic trees
	head -10 /home/share/corpora/geneea/extracted/bible/bible.txt | syntaxnet/models/parsey_universal/parse.sh syntaxnet/models/parsey_universal/Czech > bible.syntaxnet.txt
	bazel-bin/syntaxnet/conll2tree --task_context=syntaxnet/models/parsey_universal/context.pbtxt --alsologtostderr < bible.syntaxnet.txt


