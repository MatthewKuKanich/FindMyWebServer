FROM python:slim


ENV TERM xterm
WORKDIR /app

RUN apt-get update && apt-get install -y curl nano iproute2 git cron
# Clone endpoint-folder
RUN git init
RUN git remote add origin https://github.com/MatthewKuKanich/UniTracker.git
RUN git config core.sparseCheckout true
RUN echo "endpoint" >> .git/info/sparse-checkout
RUN git pull origin main
RUN git checkout main
# Configure python
RUN pip install --upgrade pip
RUN pip install --no-cache-dir -r endpoint/requirements.txt
# Update server files on startup
CMD ["sh", "-c", "./endpoint/updateRepo && python endpoint/mh_endpoint.py"]
