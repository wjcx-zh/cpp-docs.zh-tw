---
title: "系統呼叫 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.system"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "系統呼叫"
  - "Windows [C++], 系統呼叫"
ms.assetid: 0255f2ec-a5a0-487e-8b09-9dad001d81ed
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 系統呼叫
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列函式是 Windows 作業系統呼叫。  
  
### 系統呼叫函式  
  
|Function|使用|.NET Framework 對等用法|  
|--------------|--------|-------------------------|  
|[\_findclose](../c-runtime-library/reference/findclose.md)|從先前尋找作業釋放資源|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需更多的資訊，請參閱 [平台調用範例 \(Platform Invoke Examples\)](../Topic/Platform%20Invoke%20Examples.md) 。|  
|[\_findfirst 、 \_findfirst32 、 \_findfirst64 、 \_findfirsti64 、 \_findfirst32i64 、 \_findfirst64i32 、 \_wfindfirst 、 \_wfindfirst32 、 \_wfindfirst64 、 \_wfindfirsti64 、 \_wfindfirst32i64 、 \_wfindfirst64i32](../c-runtime-library/reference/findfirst-functions.md)|尋找具有指定屬性 \(Attribute\) 的檔案|[\<caps:sentence id\="tgt12" sentenceid\="e22cfa910fbeac637b6aba4ed3f9dc48" class\="tgtSentence"\>System::IO::DirectoryInfo::GetFiles\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.io.directoryinfo.getfiles.aspx)|  
|[\_findnext， \_findnext32， \_findnext64， \_findnexti64， \_findnext32i64， \_findnext64i32， \_wfindnext， \_wfindnext32， \_wfindnexti64， \_wfindnext64， \_wfindnexti64](../c-runtime-library/reference/findnext-functions.md)|具有指定之屬性 \(attribute\) 的尋找下一個檔案|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需更多的資訊，請參閱 [平台調用範例 \(Platform Invoke Examples\)](../Topic/Platform%20Invoke%20Examples.md) 。|  
  
## 請參閱  
 [依分類區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)   
 [檔案處理](../c-runtime-library/file-handling.md)   
 [目錄控制](../c-runtime-library/directory-control.md)   
 [低層級 I\/O](../c-runtime-library/low-level-i-o.md)