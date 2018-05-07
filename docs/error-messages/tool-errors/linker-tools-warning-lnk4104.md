---
title: 連結器工具警告 LNK4104 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4104
dev_langs:
- C++
helpviewer_keywords:
- LNK4104
ms.assetid: ca6728db-d616-419a-a570-65e8445c6079
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d9ea3e074cc0db9591cd0ffe9329ff7f1936563f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4104"></a>連結器工具警告 LNK4104
符號 'symbol' 的匯出應為 PRIVATE  
  
 `symbol`可以是下列其中之一：  
  
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
  
 當您在建立匯入程式庫 dll，就會發出這個警告，而且上述函式的其中一個匯出而不為私用模組定義檔中指定它。 一般情況下，這些函式會使用匯出只能由 OLE。 將它們放在匯入程式庫時可能會導致不尋常的行為不正確地連結至程式庫的程式會呼叫它們。 如需 PRIVATE 關鍵字的詳細資訊，請參閱[匯出](../../build/reference/exports.md)。