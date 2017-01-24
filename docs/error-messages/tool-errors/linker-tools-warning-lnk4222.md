---
title: "連結器工具警告 LNK4222 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4222"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4222"
ms.assetid: b7bb1794-41fb-4c83-b9b0-59c0d786a7da
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具警告 LNK4222
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不可指派序數給已匯出的符號 'symbol'  
  
 下列符號不可用序數匯出：  
  
-   `DllCanUnloadNow`  
  
-   `DllGetClassObject`  
  
-   `DllGetClassFactoryFromClassString`  
  
-   `DllInstall`  
  
-   `DllRegisterServer`  
  
-   `DllRegisterServerEx`  
  
-   `DllUnregisterServer`  
  
 這些函式一律都使用 `GetProcAddress`，按照名稱來尋找。  連結器將對這種匯出方式發出警告，因為這會產生較大的映像。  當序數匯出範圍很大，而相對地僅少數匯出時，就會發生這種問題。  例如：  
  
```  
EXPORTS  
   DllGetClassObject   @1  
   MyOtherAPI      @100  
```  
  
 將會在匯出位址表要求 100 個位置，但其中 98 個 \(2\-99\) 沒有真正使用到。  另一方面，  
  
```  
EXPORTS  
   DllGetClassObject  
   MyOtherAPI      @100  
```  
  
 只需要兩個位置 \(請注意，您也可以使用 [\/EXPORT](../../build/reference/export-exports-a-function.md) 連結器選項匯出\)。