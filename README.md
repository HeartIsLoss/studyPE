# studyPE

本工程提供了针对win32的pe格式的处理方法，包括对pe文件进行拉伸到内存，保存到文件，pe的所有头部信息进行打印，以及对导入表和导出表进行打印。\



包含如下方法：
BOOL Writeprocess(PCHAR filename,PVOID buffer,PE pe);//写入到文件中

BOOL RVAtoFA(PE pe, DWORD RVA, DWORD &FA);//虚拟偏移转文件偏移

BOOL FAtoRVA(PE pe, DWORD &RVA, DWORD FA);//文件偏移转虚拟偏移

BOOL Readprocess(PCHAR dest_process, PVOID & buffer);//读取应用的字节码，放在堆中(buffer)，后期需要free

BOOL CheckAndSet(PVOID buffer, PE &pe);//检查是否符合pe结构，如果不符合则返回0，否则将pe的各个指针指向正确的位置

BOOL PrintEverything(PE &pe);//打印所有的结构,打印成功返回true

BOOL PrintImport(PE pe);//打印导入表

BOOL PrintExport(PE pe);//打印导出表

BOOL AddSection(PE &pe,PVOID &buffer);//增加一个节

BOOL  AddCode(PE pe, PBYTE Code, DWORD codesize);//在新增加的节中添加代码，在本实验中，利用iat表编写了shellcode，因此，只适用于testfoo.exe程序。

相关处理方法持续更新中。。。