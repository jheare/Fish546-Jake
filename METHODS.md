So far in ipython notebook, I have used gunzip to transfer and unzip RAD-Seq files from the READ-Only OWL server to 
a seperate data directory in Hummingbird. 
After gunzipping I used the program called STACKS (Version ?) with subfunction process radtags along with a .csv file 
containing a continuous list of my barcodes to demultiplex the RAD-Seq data. 
You can see the notebook for demultiplexing [here](http://nbviewer.ipython.org/github/jheare/Fish546-Jake/blob/master/nb/RAD-Seq%20Process.ipynb).

After this I consulted with a neighboring lab (Seeb Lab) that specializes in RAD-Seq analysis to answer some questions
about the low number of unambiguous barcodes. They suggested this was due to poor DNA quality used for library prep and to
use higher quality samples to double check the sequencing process before trusting any analysis of the original dataset. 
