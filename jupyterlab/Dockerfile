# Use the base image jupyter/datascience-notebook
FROM jupyter/datascience-notebook

# Copy the requirements file to the container
COPY requirements.txt /requirements.txt

# Install the required dependencies
RUN pip3 install -r /requirements.txt

# Run the Jupyter Notebook startup script
CMD ["start-notebook.sh"]
