## Домашнее задание к занятию "09.05 Teamcity"

### Основная часть

#### 4.Поменяйте условия сборки: если сборка по ветке master, то должен происходит mvn clean deploy, иначе mvn clean test
        steps {
            maven {
                name = "Deploy"
    
                conditions {
                    contains("teamcity.build.branch", "master")
                }
                goals = "clean deploy"
                runnerArgs = "-Dmaven.test.failure.ignore=true"
                userSettingsSelection = "settings.xml"
            }
            maven {
                name = "Test only"
    
                conditions {
                    doesNotContain("teamcity.build.branch", "master")
                }
                goals = "clean test"
            }
        }

#### 7.Запустите сборку по master, убедитесь что всё прошло успешно, артефакт появился в nexus

![img.png](/img/img.png)

#### 10. Напишите новый метод для класса Welcomer: метод должен возвращать произвольную реплику, содержащую слово hunter

    HelloPlayer.java
    public class HelloPlayer{
        public static void main(String[] args) {
            Welcomer welcomer = new Welcomer();
            System.out.println(welcomer.sayWelcome());
            System.out.println(welcomer.sayFarewell());
            System.out.println(welcomer.sayHunter());
        }
    
    Welcomer.java
    public class Welcomer{
        public String sayWelcome() {
            return "Welcome home, good hunter. What is it your desire?";
        }
        public String sayFarewell() {
            return "Farewell, good hunter. May you find your worth in waking world.";
        }
        public String sayHunter() {
            return "Say hunter.";
        }

#### 13.Сделайте push всех изменений в новую ветку в репозиторий
#### 14.Убедитесь что сборка самостоятельно запустилась, тесты прошли успешно

![img3.png](/img/img3.png)

#### 16.Настройте конфигурацию так, чтобы она собирала .jar в артефакты сборки

![img1.png](/img/img1.png)

#### 17.Проведите повторную сборку мастера, убедитесь, что сбора прошла успешно и артефакты собраны

![img2.png](/img/img2.png)

