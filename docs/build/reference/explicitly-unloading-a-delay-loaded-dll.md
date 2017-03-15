---
title: "明確卸載延遲載入的 DLL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/DELAY:UNLOAD 連結器選項"
  - "__FUnloadDelayLoadedDLL2"
  - "DELAY:UNLOAD 連結器選項"
  - "DLL 的延遲載入, 未載入"
ms.assetid: 1c4c5172-fd06-45d3-9e4f-f12343176b3c
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 明確卸載延遲載入的 DLL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[\/delay](../../build/reference/delay-delay-load-import-settings.md):unload 連結器選項讓您卸載延遲載入的 DLL。  在預設情形下，當您的程式碼 \(使用 \/delay:unload 和 **\_\_FUnloadDelayLoadedDLL2**\) 卸載 DLL 時，延遲載入的匯入仍會保留在匯入位址表 \(IAT\) 中。  但是，如果您在連結器命令列中使用 \/delay:unload，則 Helper 函式將支援 DLL 的明確卸載，將 IAT 重設為原始形式；而目前無效的指標將會被覆寫。  IAT 是 [ImgDelayDescr](../../build/reference/calling-conventions-parameters-and-return-type.md) 中的欄位，其中包含原始 IAT \(如果存在的話\) 的複本位址。  
  
## 範例  
  
### 程式碼  
  
```  
// link with /link /DELAYLOAD:MyDLL.dll /DELAY:UNLOAD  
#include <windows.h>  
#include <delayimp.h>  
#include "MyDll.h"  
#include <stdio.h>  
  
#pragma comment(lib, "delayimp")  
#pragma comment(lib, "MyDll")  
int main()  
{  
    BOOL TestReturn;  
    // MyDLL.DLL will load at this point  
    fnMyDll();  
  
    //MyDLL.dll will unload at this point  
    TestReturn = __FUnloadDelayLoadedDLL2("MyDll.dll");  
  
    if (TestReturn)  
        printf_s("\nDLL was unloaded");  
    else  
        printf_s("\nDLL was not unloaded");  
}  
```  
  
### 註解  
 有關卸載延遲載入 DLL 的重要注意事項：  
  
-   您可以在 \\VC7\\INCLUDE\\DELAYHLP.CPP 檔案中找到 **\_\_FUnloadDelayLoadedDLL2** 函式的實作。  
  
-   **\_\_FUnloadDelayLoadedDLL2** 函式的名稱參數 \(包含大小寫\) 必須完全符合匯入程式庫中所包含的內容 \(該字串也在影像的匯入表中\)。  您可以利用 [DUMPBIN \/DEPENDENTS](../../build/reference/dependents.md) 檢視匯入程式庫的內容。  如果想要進行不區分大小寫的字串比對，您可以更新 **\_\_FUnloadDelayLoadedDLL2** 以使用 CRT 字串函式之一或 Windows API 呼叫。  
  
 如需詳細資訊，請參閱[卸載延遲載入的 DLL](../../build/reference/unloading-a-delay-loaded-dll.md)。  
  
## 請參閱  
 [延遲載入 DLL 的連結器支援](../../build/reference/linker-support-for-delay-loaded-dlls.md)