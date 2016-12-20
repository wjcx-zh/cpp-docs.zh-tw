---
title: "連結器工具警告 LNK4104 | Microsoft Docs"
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
  - "LNK4104"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4104"
ms.assetid: ca6728db-d616-419a-a570-65e8445c6079
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具警告 LNK4104
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

符號 'symbol' 的匯出應為 PRIVATE  
  
 `symbol` 可以是下列其中之一：  
  
-   `DllCanUnloadNow`  
  
-   `DllGetClassObject`  
  
-   `DllGetClassFactoryFromClassString`  
  
-   `DllGetDocumentation`  
  
-   `DllInitialize`  
  
-   `DllInstall`  
  
-   `DllRegisterServer`  
  
-   `DllRegisterServerEx`  
  
-   `DllRegisterServerExW`  
  
-   `DllUnload`  
  
-   `DllUnregisterServer`  
  
-   `RasCustomDeleteEntryNotify`  
  
-   `RasCustomDial`  
  
-   `RasCustomDialDlg`  
  
-   `RasCustomEntryDlg`  
  
 當您建置 DLL 的匯入程式庫，並匯出上述函式之一而未在模組定義檔中指定為 PRIVATE 時，就會發出這個警告。  一般而言，這些函式僅匯出供 OLE 使用。  將這些函式置於匯入程式庫，會使得連結至程式庫的程式在不正確呼叫它們時，產生異常行為。  如需 PRIVATE 關鍵字的詳細資訊，請參閱 [EXPORTS](../../build/reference/exports.md)。