---
title: "連結器工具警告 LNK4222 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4222
dev_langs:
- C++
helpviewer_keywords:
- LNK4222
ms.assetid: b7bb1794-41fb-4c83-b9b0-59c0d786a7da
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2a54c452a5df6f99260d6d01fbf4bb9f2f17b955
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4222"></a>連結器工具警告 LNK4222
匯出的符號 'symbol' 不可指派序數  
  
 不應該依序數匯出下列符號：  
  
-   `DllCanUnloadNow`  
  
-   `DllGetClassObject`  
  
-   `DllGetClassFactoryFromClassString`  
  
-   `DllInstall`  
  
-   `DllRegisterServer`  
  
-   `DllRegisterServerEx`  
  
-   `DllUnregisterServer`  
  
 這些函式一定會位於依名稱、 使用`GetProcAddress`。 連結器警告這種匯出是的因為它可能會導致較大的影像。 如果序數匯出的範圍很大，而相對較少的匯出，則會發生此問題。 例如，套用至物件的  
  
```  
EXPORTS  
   DllGetClassObject   @1  
   MyOtherAPI      @100  
```  
  
 將會需要 100 個匯出位址表格中具有 98 個 (2-99) 沒有真正位置。 相反地，  
  
```  
EXPORTS  
   DllGetClassObject  
   MyOtherAPI      @100  
```  
  
 將需要兩個位置。 (請注意，您也可以匯出與[/EXPORT](../../build/reference/export-exports-a-function.md)連結器選項。)