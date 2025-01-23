```shell
gradle init
gradle bootRun # Running
gradle bootJar # create an executable jar
``` 

![[gradle.png]]
# Build configuration
- Settings file
- Build files
- Gradle wrapper: same version Gradle for all memeber
- `./gradlew` : on UNIX system
- `./gradlew.bat`: on Window
## DSL
- Groovy DSL
- Kotlin DSL
# Plugins & tasks
## Plugins
- Core 
- Community
- Local
## Tasks
- Tasks belong to projects
- The structure of tasks
    - have inputs
    - execute an action
    - can generate outputs
# Dependency management
## Dependency
Type
- Module
- Other gradle project
### Module Dependency
- Module ID: group or library name
- Dependency configuration: `implementation`, `api`,  `runtimeOnly`, `testImplementation`
- Module version
Type
- Direct
- Transitive
#### Dependency configuration type
- Resolved: include transitive dependency
- Bucket: not include

### `api` vs `implementation`
- Old: `complie` split to `api` and `implementation`
![[api vs implementation.png]]

| API                                                                                                                                                                  | Implementation                                                                                                                                                                 |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Nếu module A khai báo `api 'org.apache.commons:commons-lang3:3.12.0'` và module B phụ thuộc vào module A, thì module B **có thể sử dụng các API của commons-lang3**. | Nếu module A khai báo `implementation 'com.google.guava:guava:31.0.1-jre'` và module B phụ thuộc vào module A, thì module B **không thể sử dụng trực tiếp các API của Guava**. |
| Mở rộng ra cho các module khác                                                                                                                                       | Chỉ có trong module hiện tại                                                                                                                                                   |
| Chậm hơn (do phải xử lý thêm dependency)                                                                                                                             | Nhanh hơn (giảm dependency không cần thiết)                                                                                                                                    |
| Khi dependency là một phần của public API                                                                                                                            | Khi dependency chỉ được sử dụng nội bộ                                                                                                                                         |
### Version catalog
- `libs.versions.toml`
- If multiple versions of a dependency are requested what will Gradle build tool do by default? Pick the highest version

## Repository


# Reference
- [Introduction to Gradle for Developers - DPEU](https://dpeuniversity.gradle.com/app/courses/012de84f-fcd3-45d4-9c4c-284382eb3f3f)
- 