# Dockerfile for Jupyter notebooks on Windows 10

FROM mcr.microsoft.com/windows:2004-amd64

RUN mkdir C:\temp

WORKDIR C:/temp

ADD ./python-3.9.1-amd64.exe python-3.9.1-amd64.exe

ADD ./requirements.txt requirements.txt

RUN python-3.9.1-amd64.exe /quiet IncludeAllUsers=1 PrependPath=1 TargetDir=C:\Python3.9

WORKDIR C:/Python3.9

RUN pip install --upgrade pip

RUN pip install --requirement C:/temp/requirements.txt

# These are requirements that should be met in the requirements.txt above
# RUN pip install scikit-learn

# RUN pip install pandas

# RUN pip install matplotlib

# RUN pip install warnings

# RUN pip install category_encoders

# RUN pip install xgboost

# RUN pip install jupyter

# RUN pip install tqdm

ADD ./notebook.ps1 notebook.ps1

RUN mkdir C:\work

RUN powershell Set-ExecutionPolicy -ExecutionPolicy Bypass

# This doesn't work
# ENTRYPOINT ["C:/Python3.9/notebook.ps1"]

# this command will give the container a lot more memory
# docker run -it -v C:\Source\JupyterPython3\work:C:\work --name=jupyterpy3 -m 16g jupyterpy3 powershell
# run .\notebook.sh in work directory

# docker inspect --format '{{ .NetworkSettings.Networks.nat.IPAddress }}' <container>  
# $ip = $(Get-NetIPAddress -InterfaceAlias Ethernet -AddressFamily IPv4 | Select-Object IPAddress).IPAddress
# jupyter notebook --ip=$ip --port=8888
# CMD powershell ./notebook.ps1
