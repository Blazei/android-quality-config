# Java Quality Config
This Repository was created to share config file of Code Analysis Tools across my project. Feel free to folk this and make your own rule!

__Code Analysis tools__
- [Checkstyle](http://checkstyle.sourceforge.net/).
- [PMD](https://pmd.github.io/).
- [Findbugs](http://findbugs.sourceforge.net/).

### Suggestion for Android
For easy and clean way to apply all Analysis tools on Android Project check this [Android Check](https://github.com/noveogroup/android-check), All config of this project should work with it.


## Setup

### Donwload Config file
Download or update config file by [Gradle Download Task](https://github.com/michel-kraemer/gradle-download-task).

*Step 1* Setup gradle download task plugins

```groovy
buildscript {
    repositories {
        jcenter()
    }
    dependencies {
        classpath 'de.undercouch:gradle-download-task:2.1.0'
    }
}

apply plugin: 'de.undercouch.download'
```
*Step 2* Add config file download task on root's build.gradle or module one
 
```groovy 
import de.undercouch.gradle.tasks.download.Download
task updateConfig(type: Download) {
    src([
            'https://raw.githubusercontent.com/Blazei/java-quality-config/master/config/checkstyle.xml',
            'https://raw.githubusercontent.com/Blazei/java-quality-config/master/config/pmd.xml',
            'https://raw.githubusercontent.com/Blazei/java-quality-config/master/config/findbugs.xml',
    ])
    dest "$rootDir/config/" //Can change to config path you like
}
```

*Step 3* call updateConfig task

```
./graldew updateConfig
```

Feel free to remove all these gradle snippet, these config is hardy to update... Except I found bug!

### Apply Code Quality Plug-in

**Java module**

Add follow line to build.gradle of module (config file must locate at ```rootDir/config```)

```groovy
apply from: 'https://raw.githubusercontent.com/Blazei/java-quality-config/master/java/quality.gradle'
```

**Android module**

setup follow [README.md](https://github.com/noveogroup/android-check/blob/master/README.md) of [Android Check](https://github.com/noveogroup/android-check)



##License
This Project licensed under the
[Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0).

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.




