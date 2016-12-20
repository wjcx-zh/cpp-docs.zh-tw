---
title: "指定要延遲載入的 DLL | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/DELAYLOAD 連結器選項"
  - "DLL 的延遲載入"
  - "DLL 的延遲載入, 指定"
  - "DELAYLOAD 連結器選項"
ms.assetid: 94cbecfe-7a42-40d1-a618-9f2786bac0d8
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 指定要延遲載入的 DLL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可以使用 [\/delayload](../../build/reference/delayload-delay-load-import.md):`dllname` 連結器選項來指定要延遲載入的 DLL。  如果您不打算使用自己的 Helper 函式版本，您也必須連結您的程式與 delayimp.lib \(適用於桌面應用程式\) 或 dloadhelper.lib \(適用於市集應用程式\)。  
  
 延遲載入 DLL 的簡單範例如下：  
  
```  
// cl t.cpp user32.lib delayimp.lib  /link /DELAYLOAD:user32.dll  
#include <windows.h>  
// uncomment these lines to remove .libs from command line  
// #pragma comment(lib, "delayimp")  
// #pragma comment(lib, "user32")  
  
int main() {  
   // user32.dll will load at this point  
   MessageBox(NULL, "Hello", "Hello", MB_OK);  
}  
```  
  
 建置專案的偵錯版本。  使用偵錯工具逐步執行程式碼，您會注意到只有在呼叫 `MessageBox` 時才會載入 user32.dll 。  
  
## 請參閱  
 [延遲載入 DLL 的連結器支援](../../build/reference/linker-support-for-delay-loaded-dlls.md)