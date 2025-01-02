# iocs-handbook
Integrated Operational Control System Handbook

Link to published site here:
https://iocs-handbook.readthedocs.io/en/latest/


# Install required Python dependencies (Sphinx etc.)
pip install -r requirements.txt
sudo apt install python3-sphinx
pip install sphinx-rtd-theme
pip install sphinxcontrib-video
 pip install sphinxcontrib-bibtex


# Run the raw sphinx-build command
sphinx-build -M html . _build/