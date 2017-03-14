# Geneea Syntaxnet docker images

## Building the syntaxnet container

    # build syntaxnet docker image with models from Universal Dependencies
    sudo docker build -t geneea-syntaxnet-ud .
    

## Running the syntaxnet container

	# run geneea-syntaxnet-ud docker image
	sudo docker run -it geneea-syntaxnet-ud bash

	# parse some text, use language model from 'syntaxnet/models/parsey_universal/Czech'
	echo 'Bob přinesl Alici pizzu.' | syntaxnet/models/parsey_universal/parse.sh syntaxnet/models/parsey_universal/Czech

