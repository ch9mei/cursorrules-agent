# 规范生成与维护规则

## 1. 规范生成机制
```
1. 触发机制：
   a. 自动触发：
      - 项目初始化时自动执行 #SCAN-PROJECT
      - 依赖文件变更时自动执行 #SCAN-TECH
      - 代码提交前自动执行 #CHECK-RULES
      
   b. 手动触发：
      - #SCAN-PROJECT：手动执行全量扫描
      - #SCAN-TECH：手动更新技术栈
      - #CHECK-RULES：手动检查规范

2. 触发命令：
   #SCAN-PROJECT：
   - 自动创建规范目录结构：
     * .cursorrules.d/project_base/  # 项目基础信息
     * .cursorrules.d/tech_stack/    # 技术栈信息
     * .cursorrules.d/notes/         # 规范和记录
   
   - 自动创建基础文件：
     * project_base/：
       - instructions.md  # 项目规范说明
       - entities.md      # 实体定义规范
       - api.md          # 接口规范
       - utils.md        # 工具类规范
       - versions.md     # 版本规范
     * tech_stack/：
       - deps.md         # 依赖规范
     * notes/：
       - lessons.md      # 经验教训
       - current_task.md # 当前任务
       - scratchpad.md   # 临时记录

   - 权限检查：
     * 检查目录创建权限
     * 检查文件读写权限
     * 确保文件可访问性

   - 项目扫描与分类：
     * 扫描项目结构：
       - 分析目录层次
       - 识别模块关系
       - 记录到 project_base/instructions.md：
         ```
         # [项目名称] 项目说明
         
         ## 1. 项目概述
         ### 1.1 项目描述
         [优先级扫描：
           1. 项目根目录下的描述文件：
              * README.md
              * README.txt
              * README
              * package.json 的 description 字段
              * setup.py 的 description
              * composer.json 的 description
           2. 项目配置文件：
              * build.gradle
              * pom.xml
              * package.json
              * setup.py
              * composer.json
              * cargo.toml
           3. 项目文档目录：
              * docs/
              * doc/
              * documents/
              * documentation/]

         ### 1.2 技术栈
         [学习阶段：
           1. 配置文件分析：
              * 扫描所有配置文件
              * 提取依赖信息
              * 识别框架特征
           2. 源码分析：
              * 扫描源码目录
              * 识别语言特征
              * 提取框架特征
           3. 工具链分析：
              * 识别构建工具
              * 识别开发工具
              * 识别部署工具
           4. 记录发现的技术栈：
              * 语言：[版本]
              * 框架：[版本]
              * 工具：[版本]]

         ### 1.3 环境要求
         [学习阶段：
           1. 运行环境：
              * 系统要求
              * 运行时版本
              * 依赖服务
           2. 开发环境：
              * 编译工具
              * 开发IDE
              * 插件要求
           3. 部署环境：
              * 容器要求
              * 资源需求
              * 网络要求]
         
         ## 2. 项目结构
         [学习阶段：
           1. 目录结构分析：
              * 扫描所有目录
              * 识别目录用途
              * 统计目录特征
           2. 模块关系分析：
              * 分析依赖关系
              * 识别核心模块
              * 提取模块职责
           3. 记录项目结构：
              * 核心目录说明
              * 模块依赖图
              * 关键组件说明]
         ```
     
     * 扫描项目特征：
       - 学习阶段：
         1. 项目类型识别：
            * 分析项目结构特征
            * 识别架构模式
            * 确定项目类型
         2. 开发模式识别：
            * 分析工作流程
            * 识别开发规范
            * 提取最佳实践
         3. 记录项目特征：
            * 项目类型说明
            * 架构模式描述
            * 开发模式总结

     * 扫描实体定义：
       - 学习阶段（首次扫描）：
         1. 目录模式学习：
            * 递归扫描所有目录
            * 分析包含实体定义的目录名模式
            * 统计目录命名规律
         
         2. 文件模式学习：
            * 分析实体文件的命名规则
            * 识别文件扩展名特征
            * 总结文件命名模式
         
         3. 定义模式学习：
            * 分析文件内容的实体定义方式
            * 识别常用注解或关键字
            * 提取定义模式特征
            * 提取类注释和描述信息
            * 记录类的全限定名
         
         4. 记录到 project_base/instructions.md：
            ```
            ## 项目实体规范
            ### 1. 实体目录规范
            - 发现的目录模式：
              * [目录模式1]：[出现次数] 次
                示例：[目录路径示例]
              * [目录模式2]：[出现次数] 次
                示例：[目录路径示例]
            
            ### 2. 实体文件规范
            - 文件命名规则：
              * 前缀：[常见前缀统计]
              * 后缀：[常见后缀统计]
              * 示例：[典型文件名示例]
            
            ### 3. 实体定义规范
            - 定义方式：
              * [发现的定义模式1]：[使用频率]
                示例：[代码片段]
              * [发现的定义模式2]：[使用频率]
                示例：[代码片段]
            
            ### 4. 实体目录映射
            - [目录路径1]：
              * 用途：[根据内容推测的用途]
              * 实体类型：[包含的实体类型]
              * 实体列表：
                - 全限定名：[com.xxx.domain.Entity1]
                  描述：[从类注释中提取的描述]
                  用途：[从代码分析推测的用途]
                - 全限定名：[com.xxx.domain.Entity2]
                  描述：[从类注释中提取的描述]
                  用途：[从代码分析推测的用途]
            - [目录路径2]：
              * 用途：[根据内容推测的用途]
              * 实体类型：[包含的实体类型]
              * 实体列表：
                - 全限定名：[com.xxx.domain.Entity3]
                  描述：[从类注释中提取的描述]
                  用途：[从代码分析推测的用途]
            ```
       
       - 增量扫描阶段：
         1. 根据已学习的规范扫描新增文件
         2. 验证是否符合已知模式
         3. 发现新模式时更新规范
         4. 记录到 project_base/entities.md：
            ```
            ## 实体类清单
            
            ### [模块名称1]
            #### [子模块1]
            - 全限定名：[com.xxx.domain.Entity1]
              描述：[从类注释中提取的描述]
              用途：[从代码分析推测的用途]
              关系：
                - 关联：[关联的其他实体]
                - 继承：[父类]
                - 实现：[实现的接口]
            
            #### [子模块2]
            - 全限定名：[com.xxx.domain.Entity2]
              描述：[从类注释中提取的描述]
              用途：[从代码分析推测的用途]
              关系：
                - 关联：[关联的其他实体]
                - 继承：[父类]
                - 实现：[实现的接口]
            ```
       
       - 规范维护：
         1. 定期验证规范有效性
         2. 自动适应项目变化
         3. 更新实体定义规范
         4. 标记过时的规范
         5. 维护实体关系图谱
         6. 更新实体描述文档

     * 扫描API接口：
       - 扫描 controller/ 目录
       - 分析接口定义
       - 记录到 project_base/api.md
     
     * 扫描工具类：
       - 扫描 utils/ 目录
       - 分析工具方法
       - 记录到 project_base/utils.md

   #SCAN-TECH：
   - 扫描技术栈
   - 分析依赖关系
   - 更新版本信息
   - 维护依赖文档
   - 自动更新 tech_stack/deps.md

3. 生成流程：
   a. 首次扫描：
      - 创建规范目录结构
      - 检查目录权限
      - 扫描项目特征
      - 生成基础规范
      - 初始化文档

   b. 增量扫描：
      - 识别项目变化
      - 更新规范文件
      - 保持规范同步
      - 记录变更历史

4. 规范存储：
   - 规范文件统一存放在 .cursorrules.d/ 目录
   - 按功能分类组织文件
   - 使用统一的命名规则
   - 保持目录结构清晰
```

## 2. 自动维护机制
```
1. 监控范围：
   - 项目结构变化：
     * 新增/删除文件时自动触发 #SCAN-PROJECT
     * 目录结构变更时自动触发 #SCAN-PROJECT
   
   - 代码文件变更：
     * domain/ 目录变更自动更新 entities.md
     * controller/ 目录变更自动更新 api.md
     * utils/ 目录变更自动更新 utils.md
   
   - 依赖配置更新：
     * build.gradle 变更自动触发 #SCAN-TECH
     * pom.xml 变更自动触发 #SCAN-TECH
   
   - 文档内容修改：
     * 规范文件变更自动触发 #CHECK-RULES

2. 更新策略：
   - 实时监控变化
   - 自动触发扫描
   - 增量更新规范
   - 保持文档同步

3. 处理方式：
   - 自动更新规范
   - 记录变更历史
   - 保持规范一致
   - 避免冗余信息
```

## 3. 规范模板定义
```
1. 目录结构：
   .cursorrules.d/
   ├── project_base/     # 项目基础信息
   ├── tech_stack/       # 技术栈信息
   └── notes/           # 规范和记录

2. 基础文件：
   - instructions.md：项目规范说明
   - entities.md：实体定义规范
   - api.md：接口规范
   - utils.md：工具类规范
   - versions.md：版本规范
   - deps.md：依赖规范

3. 记录文件：
   - lessons.md：经验教训
     * 文件结构：
       ```
       # 项目经验教训记录
       
       ## [YYYY-MM-DD] #TAG-问题类型
       ### 问题描述
       - ID: PROBLEM-YYYYMMDD-001
       - 类型: [BUG/IMPROVEMENT/QUESTION]
       - 描述: 具体描述
       
       ### 解决方案
       - 步骤: 
         1. 步骤1
         2. 步骤2
       - 参考: [相关链接]
       
       ### 经验总结
       - 关键点: [要点1, 要点2]
       - 最佳实践: [实践1, 实践2]
       - 标签: #tag1 #tag2
       ```
     * 更新规则：
       - 每次解决问题后自动记录
       - 按时间和问题类型分类
       - 支持标签搜索和分类
       - composer执行后自动整理和优化
   
   - current_task.md：当前任务
     * 文件结构：
       ```
       # 当前任务跟踪
       
       ## 进行中任务
       - ID: TASK-YYYYMMDD-001
         类型: [FEATURE/BUG/REFACTOR]
         开始: YYYY-MM-DD HH:mm
         状态: [DOING/BLOCKED/REVIEW]
         描述: 简要描述
         进度: XX%
         依赖: [依赖任务ID列表]
         备注: 补充信息
       
       ## 待处理任务
       - ID: TASK-YYYYMMDD-002
         优先级: [P0/P1/P2]
         类型: [FEATURE/BUG/REFACTOR]
         工时: XX小时
         描述: 简要描述
         依赖: [依赖任务ID列表]
       
       ## 已完成任务
       - ID: TASK-YYYYMMDD-003
         完成: YYYY-MM-DD HH:mm
         耗时: XX小时
         产出: [文档/代码链接]
         评审: [APPROVED/REJECTED]
       ```
     * 更新规则：
       - 每日自动更新状态
       - composer执行后自动整理任务
       - 自动关联相关代码变更
       - 自动生成任务报告
   
   - scratchpad.md：临时记录
     * 文件结构：
       ```
       # 临时记录本
       
       ## [YYYY-MM-DD] #CATEGORY
       ### 想法收集
       - ID: IDEA-YYYYMMDD-001
         标签: #tag1 #tag2
         内容: 想法描述
         价值: [HIGH/MEDIUM/LOW]
         可行性: [HIGH/MEDIUM/LOW]
       
       ### 待办事项
       - [ ] #P0 紧急待办
       - [ ] #P1 普通待办
       - [ ] #P2 低优先级
       ```
     * 更新规则：
       - 实时记录，自动分类
       - composer执行后自动整理
       - 重要内容自动提取到对应文档
       - 自动清理已完成/过期内容

   * 自动化处理规则：
     - composer执行时触发：
       1. 扫描所有记录文件
       2. 按规范格式化内容
       3. 自动分类和标签化
       4. 关联代码变更记录
       5. 生成统计和报告
       6. 清理过期内容
       7. 优化存储结构
     
     - 智能关联：
       1. 通过ID关联任务和问题
       2. 通过标签关联相似内容
       3. 通过时间线展示项目进展
       4. 通过依赖关系优化任务排序
     
     - 自动报告：
       1. 生成每日任务摘要
       2. 统计问题解决效率
       3. 分析项目进展状况
       4. 识别潜在风险点
```

## 4. 命令定义
```
1. #SCAN-PROJECT：
   - 功能：全量扫描项目
   - 时机：项目初始化或重大变更
   - 范围：所有项目文件
   - 输出：更新所有规范文件
   - 执行：
     * 创建目录结构
     * 检查文件权限
     * 扫描项目内容
     * 分类写入文件

2. #SCAN-TECH：
   - 功能：扫描技术栈
   - 时机：依赖变更时
   - 范围：配置文件
   - 输出：更新技术栈文档
   - 执行：
     * 分析依赖配置
     * 更新版本信息
     * 写入deps.md

3. #CHECK-RULES：
   - 功能：检查规范完整性
   - 时机：规范更新后
   - 范围：规范文件
   - 输出：检查报告
   - 执行：
     * 检查目录完整性
     * 验证文件权限
     * 确认内容更新
```

## 5. 文件格式规范
```
1. 编码规范：
   - 使用 UTF-8 编码
   - 使用 LF 换行
   - 使用 Markdown 格式
   - 保持格式统一

2. 命名规范：
   - 文件名小写
   - 使用连字符
   - 见名知意
   - 后缀统一

3. 内容规范：
   - 层次分明
   - 注释清晰
   - 示例完整
   - 格式统一
``` 