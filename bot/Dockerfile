FROM python:3.12

WORKDIR /app

# Add your custom dependencies to the requirements.txt file to install them on build process.
COPY requirements.txt requirements.txt
RUN pip3 install -r requirements.txt

# The directory of the code to copy into this image, to be able to run the bot.
COPY . .

# The entrypoint to run the bot
ENTRYPOINT ["python3", "main.py"]
