# Task 4：思考题

## 1. Make 和简单的 build.sh 有什么区别？

build每次执行所有命令，需要手动写后台逻辑，难以管理;只适合小文件的联系和原型验证

而CMake每次只重建过期(失效)的目标，可以自动追踪源文件，声明式规则，结构清晰，适用于正式项目


## 2. CMake 是编译器吗？

执行 `cmake --build build` 时，最终是谁在编译 C 源文件？

CMake不是编译器

执行 `cmake --build build` 时，Cmake根据 CMakeLists.txt 生成 Makefile文件;
Makefile读取生成的构建文件，判断依赖关系，决定哪些文件需要重编;
最终由GCC / Clang这些编译器实现.c → .o，将 .o → 可执行文件

## 3. 为什么不希望每次都重新编译所有 `.c` 文件？

降低时间成本
