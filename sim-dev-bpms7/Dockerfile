FROM ancine/rh_bpms

USER jboss
COPY support/standalone-full.xml $JBOSS_HOME/standalone/configuration/
COPY support/userinfo.properties $JBOSS_HOME/standalone/deployments/business-central.war/WEB-INF/classes/
COPY support/userinfo.properties $JBOSS_HOME/standalone/deployments/kie-execution-server.war/WEB-INF/classes/

RUN $JBOSS_HOME/bin/add-user.sh -u admin -p ancine1!  --silent \
    && $JBOSS_HOME/bin/add-user.sh -a -r ApplicationRealm -u admin -p ancine1! -ro analyst,admin,user,manager,kiemgmt,kie-server,rest-all,SIM_PROPONENTE,SIM_COORD_TRIAGEM,SIM_COORD_ANALISE_DIREITOS,SIM_COORD_ANALISE_TECNICA,SIM_SUP_FOMENTO --silent \
    && $JBOSS_HOME/bin/add-user.sh -a -r ApplicationRealm -u kiecontrolleruser -p kiecontrolleruser1! -ro kie-server,rest-all --silent \
    && $JBOSS_HOME/bin/add-user.sh -a -r ApplicationRealm -u proponente.user.1 -p ancine1! -ro SIM_PROPONENTE,user --silent \
    && $JBOSS_HOME/bin/add-user.sh -a -r ApplicationRealm -u proponente.user.2 -p ancine1! -ro SIM_PROPONENTE,user --silent \
    && $JBOSS_HOME/bin/add-user.sh -a -r ApplicationRealm -u MRPLOT -p ancine1! -ro SIM_PROPONENTE,user --silent \
    && $JBOSS_HOME/bin/add-user.sh -a -r ApplicationRealm -u coord.triagem.1 -p ancine1! -ro SIM_COORD_TRIAGEM,user,manager --silent \
    && $JBOSS_HOME/bin/add-user.sh -a -r ApplicationRealm -u coord.triagem.2 -p ancine1! -ro SIM_COORD_TRIAGEM,user,manager --silent \
    && $JBOSS_HOME/bin/add-user.sh -a -r ApplicationRealm -u denise.lezo -p ancine1! -ro SIM_COORD_TRIAGEM,user,manager --silent \
    && $JBOSS_HOME/bin/add-user.sh -a -r ApplicationRealm -u coord.analise.direitos.1 -p ancine1! -ro SIM_COORD_ANALISE_DIREITOS,user,manager --silent \
    && $JBOSS_HOME/bin/add-user.sh -a -r ApplicationRealm -u coord.analise.direitos.2 -p ancine1! -ro SIM_COORD_ANALISE_DIREITOS,user,manager --silent \
    && $JBOSS_HOME/bin/add-user.sh -a -r ApplicationRealm -u coord.analise.tecnica.1 -p ancine1! -ro SIM_COORD_ANALISE_TECNICA,user,manager --silent \
    && $JBOSS_HOME/bin/add-user.sh -a -r ApplicationRealm -u coord.analise.tecnica.2 -p ancine1! -ro SIM_COORD_ANALISE_TECNICA,user,manager --silent \
    && $JBOSS_HOME/bin/add-user.sh -a -r ApplicationRealm -u sup.fomento -p ancine1! -ro SIM_SUP_FOMENTO,user,manager --silent \
    && $JBOSS_HOME/bin/add-user.sh -a -r ApplicationRealm -u krisv -p krisv -ro admin,analyst,kie-server,rest-all  --silent \
    && $JBOSS_HOME/bin/add-user.sh -a -r ApplicationRealm -u john -p john -ro analyst,Accounting,PM,kie-server,rest-all --silent \
    && $JBOSS_HOME/bin/add-user.sh -a -r ApplicationRealm -u sales-rep -p sales-rep -ro analyst,sales,kie-server,rest-all --silent \
    && $JBOSS_HOME/bin/add-user.sh -a -r ApplicationRealm -u katy -p katy -ro analyst,HR,kie-server,rest-all --silent \
    && $JBOSS_HOME/bin/add-user.sh -a -r ApplicationRealm -u jack -p jack -ro analyst,IT,kie-server,rest-all --silent \
    && $JBOSS_HOME/bin/add-user.sh -a -r ApplicationRealm -u maciek -p maciek1!  -ro employees,kie-server,rest-all,user,IT --silent \
    && $JBOSS_HOME/bin/add-user.sh -a -r ApplicationRealm -u tihomir -p tihomir1! -ro employees,apple,dell,lenovo,other,kie-server,rest-all,user,IT --silent \
    && $JBOSS_HOME/bin/add-user.sh -a -r ApplicationRealm -u krisv -p krisv1! -ro employees,manager,kie-server,rest-all,user,IT --silent \
    && $JBOSS_HOME/bin/add-user.sh -a -r ApplicationRealm -u mary -p mary1! -ro employees,manager,kie-server,rest-all,user,IT --silent \
    && $JBOSS_HOME/bin/add-user.sh -a -r ApplicationRealm -u paul -p paul1! -ro employees,manager,kie-server,rest-all,user,IT --silent \
    && $JBOSS_HOME/bin/add-user.sh -a -r ApplicationRealm -u kieserver -p kieserver1! -ro employees,kie-server,rest-all,user --silent 

USER root
RUN chown -R jboss:jboss $JBOSS_HOME/standalone/deployments/business-central.war/WEB-INF/classes/userinfo.properties $JBOSS_HOME/standalone/deployments/kie-execution-server.war/WEB-INF/classes/userinfo.properties
USER jboss

CMD ["/opt/jboss/jboss/bin/standalone.sh", "-c", "standalone-full.xml",  "-b", "0.0.0.0", "-bmanagement", "0.0.0.0"]
