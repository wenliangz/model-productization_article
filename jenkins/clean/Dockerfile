FROM wenliang/wenliang-pipelines-jenkins:22.02

COPY ./scripts/ ${JENKINS_HOME}/init.groovy.d/
COPY requirements.txt ${JENKINS_HOME}
WORKDIR ${JENKINS_HOME}
RUN pip install -r requirements.txt