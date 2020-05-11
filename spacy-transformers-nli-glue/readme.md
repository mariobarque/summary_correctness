# Fine Tuning BERT base with spacy-transformers

## Instalation
* Make sure you have python 3.6 or 3.7. Note that I have an issue running this with python 3.8 and was not able to fixed it so I had to install python 3.7 and it worked. 
* (For Azure VM environment only) I just noticed that the VMs have python 3.5, that one doesn't work either. So install 3.6 or 3.7.
    ```bash
    conda install python==3.6
    ```
* Download the code from git:
    ```bash
    git clone https://github.com/xcs224-summary-team/summary-nli-experiments.git
    cd summary-nli-experiments/spacy-transformers-nli-glue
    ```
* (Optional) I recommend to have a virtual environment. Run the following commands:
    ```bash
    python -m venv env
    source env/bin/activate
    ```
* If you don't have it, install pytorch. Run the following command:
    ```bash
    pip install torch==1.2.0 torchvision==0.4.0 -f https://download.pytorch.org/whl/torch_stable.html
    ```
* Install the library and other dependencies:
    ```bash
    pip install --upgrade pip
    pip install spacy-transformers
    pip install -r requirements.txt
    ```
* Download and installed bert base Transformer:
    ```bash
    python -m spacy download en_trf_bertbaseuncased_lg
    ```

Once you have everything in place you can start fine tuning bert with the hugging face datasets. 
In order to do that first install the datasets. Run the following command inside the spacy-transformers-nli-glue folder.

```bash
python download_glue_data.py --data_dir glue_data --tasks all
```

Once you have all this data you can start fine tunining bert. Here is an example with MultiNLI:

```bash
python run_glue.py "en_trf_bertbaseuncased_lg" "mnli" "glue_data" "my_fine_tuned_models" "glue.conf"
```