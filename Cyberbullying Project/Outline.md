# Project Outline and Directions
Related work areas to cover 
- Cyberbullying Detection via Social Media Analysis 
- Dynamic Query Expansion for Event Detection
- Data Augmentation approach. 

https://fasttext.cc/docs/en/language-identification.html

Our preprocessing pipeline: 
 - remove all non-English tweets 
 - tokenize tweet characteristics 
	 - URL
	 - MENTION
	 - RESERVED
	 - SMILEY
- demojize 
- replace all special characters with space 
- train Word Piece tokenizer on the dataset with the following special tokens. 
	- "\$HASHTAG\$", "\$EMOJI\$", "\$URL\$", RESERVED\$", "\$MENTION$", "[UNK]"
	- tokenizer pipeline 
		- WordPiece
		- Lowercase(), NFD(), StripAccents() normalizers 
		- encode and extract tokens 
		- drop duplicate tokenizations 