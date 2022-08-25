Fork of https://github.com/vrothberg/vgrep with experimental patches.

## Extended refine

New vgrep command `Refine (extended)` supports either **k**eeping or **d**eleting matches based on a regexp
match on either **f**ilename or **c**ontent.

This enables quickly narrowing down the list of matches:

- `R d f foo` deletes all matches whose filename match the pattern "foo"
- `R k c bar` keeps all matches where the line content matches the pattern "bar"

### Example

Initial search:

```console
$ vgrep setJobExecutorActivate
Index File                                                                                                                                         Line Content
    0 spring-boot-starter/starter/src/main/java/org/camunda/bpm/spring/boot/starter/configuration/impl/DefaultJobConfiguration.java                  69 configuration.setJobExecutorActivate(false);
    1 quarkus-extension/engine/qa/src/test/java/org/camunda/bpm/engine/cdi/test/CdiProcessEngineTestCase.java                                       164 engineConfig.setJobExecutorActivate(false);
    2 quarkus-extension/engine/runtime/src/main/java/org/camunda/bpm/quarkus/engine/extension/QuarkusProcessEngineConfiguration.java                 38 setJobExecutorActivate(true);
    3 quarkus-extension/engine/deployment/src/test/java/org/camunda/bpm/quarkus/engine/test/ConfigurableProcessEngineTest.java                       48 engineConfig.setJobExecutorActivate(false);
    4 quarkus-extension/engine/deployment/src/test/java/org/camunda/bpm/quarkus/engine/test/config/CamundaEngineProgrammaticAndConfigFileTest.java   58 engineConfig.setJobExecutorActivate(false);
    5 engine-spring/core/src/test/java/org/camunda/bpm/engine/spring/test/configuration/InMemProcessEngineConfiguration.java                         64 config.setJobExecutorActivate(false);
    6 distro/wildfly/subsystem/src/main/java/org/camunda/bpm/container/impl/jboss/config/ManagedJtaProcessEngineConfiguration.java                   35 setJobExecutorActivate(true);
    7 engine/src/main/java/org/camunda/bpm/engine/ProcessEngineConfiguration.java                                                                   758 public ProcessEngineConfiguration setJobExecutorActivate(boolean jobExecutorActivate) {
    8 engine/src/main/java/org/camunda/bpm/engine/impl/cfg/ProcessEngineConfigurationImpl.java                                                     3626 public ProcessEngineConfigurationImpl setJobExecutorActivate(boolean jobExecutorActivate) {
    9 engine/src/main/java/org/camunda/bpm/engine/impl/cfg/ProcessEngineConfigurationImpl.java                                                     3627 super.setJobExecutorActivate(jobExecutorActivate);
   10 engine/src/main/java/org/camunda/bpm/container/impl/deployment/StartProcessEngineStep.java                                                    100 setJobExecutorActivate(configuration, properties);
   11 engine/src/main/java/org/camunda/bpm/container/impl/deployment/StartProcessEngineStep.java                                                    123 protected void setJobExecutorActivate(ProcessEngineConfigurationImpl configuration, Map<String, String> properties) {
   12 engine/src/main/java/org/camunda/bpm/container/impl/deployment/StartProcessEngineStep.java                                                    126 configuration.setJobExecutorActivate(true);
   13 engine/src/test/java/org/camunda/bpm/engine/test/jobexecutor/SequentialJobAcquisitionTest.java                                                 82 standaloneProcessEngineConfiguration.setJobExecutorActivate(false);
   14 engine/src/test/java/org/camunda/bpm/engine/test/jobexecutor/SequentialJobAcquisitionTest.java                                                115 engineConfiguration1.setJobExecutorActivate(false);
   15 engine/src/test/java/org/camunda/bpm/engine/test/jobexecutor/SequentialJobAcquisitionTest.java                                                125 engineConfiguration2.setJobExecutorActivate(false);
   16 engine/src/test/java/org/camunda/bpm/engine/test/jobexecutor/SequentialJobAcquisitionTest.java                                                175 engineConfiguration1.setJobExecutorActivate(false);
   17 engine/src/test/java/org/camunda/bpm/engine/test/jobexecutor/SequentialJobAcquisitionTest.java                                                185 engineConfiguration2.setJobExecutorActivate(false);
   18 engine/src/test/java/org/camunda/bpm/engine/test/api/authorization/DefaultUserPermissionNameForTaskCfgTest.java                               129 .setJobExecutorActivate(false)
   19 engine/src/test/java/org/camunda/bpm/engine/test/api/runtime/RuntimeServiceTest.java                                                         2745 .setJobExecutorActivate(false)
   20 engine/src/test/java/org/camunda/bpm/engine/test/api/runtime/RuntimeServiceTest.java                                                         2774 .setJobExecutorActivate(false)
   21 engine/src/test/java/org/camunda/bpm/engine/test/api/repository/RepositoryServiceTest.java                                                    762 .setJobExecutorActivate(false)
   22 engine/src/test/java/org/camunda/bpm/engine/test/api/repository/RepositoryServiceTest.java                                                    770 .setJobExecutorActivate(false)
   23 camunda-bpm-spring-boot-starter/starter/src/main/java/org/camunda/bpm/spring/boot/starter/configuration/impl/DefaultJobConfiguration.java      69 configuration.setJobExecutorActivate(false);
```

Remove all test classes:

```console
$ vgrep --interactive
Enter a vgrep command: R d f Test
Enter a vgrep command: p
Index File                                                                                                                                      Line Content
    0 spring-boot-starter/starter/src/main/java/org/camunda/bpm/spring/boot/starter/configuration/impl/DefaultJobConfiguration.java               69 configuration.setJobExecutorActivate(false);
    1 quarkus-extension/engine/runtime/src/main/java/org/camunda/bpm/quarkus/engine/extension/QuarkusProcessEngineConfiguration.java              38 setJobExecutorActivate(true);
    2 engine-spring/core/src/test/java/org/camunda/bpm/engine/spring/test/configuration/InMemProcessEngineConfiguration.java                      64 config.setJobExecutorActivate(false);
    3 distro/wildfly/subsystem/src/main/java/org/camunda/bpm/container/impl/jboss/config/ManagedJtaProcessEngineConfiguration.java                35 setJobExecutorActivate(true);
    4 engine/src/main/java/org/camunda/bpm/engine/ProcessEngineConfiguration.java                                                                758 public ProcessEngineConfiguration setJobExecutor>
    5 engine/src/main/java/org/camunda/bpm/engine/impl/cfg/ProcessEngineConfigurationImpl.java                                                  3626 public ProcessEngineConfigurationImpl setJobExec>
    6 engine/src/main/java/org/camunda/bpm/engine/impl/cfg/ProcessEngineConfigurationImpl.java                                                  3627 super.setJobExecutorActivate(jobExecutorActivate>
    7 engine/src/main/java/org/camunda/bpm/container/impl/deployment/StartProcessEngineStep.java                                                 100 setJobExecutorActivate(configuration, properties>
    8 engine/src/main/java/org/camunda/bpm/container/impl/deployment/StartProcessEngineStep.java                                                 123 protected void setJobExecutorActivate(ProcessEng>
    9 engine/src/main/java/org/camunda/bpm/container/impl/deployment/StartProcessEngineStep.java                                                 126 configuration.setJobExecutorActivate(true);
   10 camunda-bpm-spring-boot-starter/starter/src/main/java/org/camunda/bpm/spring/boot/starter/configuration/impl/DefaultJobConfiguration.java   69 configuration.setJobExecutorActivate(false);
```

Keep all lines containing "configuration":

```console
Enter a vgrep command: R k c configuration
Enter a vgrep command: p
Index File                                                                                                                                      Line Content
    0 spring-boot-starter/starter/src/main/java/org/camunda/bpm/spring/boot/starter/configuration/impl/DefaultJobConfiguration.java               69 configuration.setJobExecutorActivate(false);
    1 camunda-bpm-spring-boot-starter/starter/src/main/java/org/camunda/bpm/spring/boot/starter/configuration/impl/DefaultJobConfiguration.java   69 configuration.setJobExecutorActivate(false);
    2 engine/src/main/java/org/camunda/bpm/container/impl/deployment/StartProcessEngineStep.java                                                 100 setJobExecutorActivate(configuration, properties);
    3 engine/src/main/java/org/camunda/bpm/container/impl/deployment/StartProcessEngineStep.java                                                 123 protected void setJobExecutorActivate(ProcessEngineConfigurationImpl configuration, Map<String, String> properties) {
    4 engine/src/main/java/org/camunda/bpm/container/impl/deployment/StartProcessEngineStep.java                                                 126 configuration.setJobExecutorActivate(true);
```
