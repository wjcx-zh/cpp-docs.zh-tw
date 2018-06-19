---
title: 連結器工具警告 LNK4222 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4222
dev_langs:
- C++
helpviewer_keywords:
- LNK4222
ms.assetid: b7bb1794-41fb-4c83-b9b0-59c0d786a7da
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 359af4c4d3b1079b2d56f108bff0ee1488ea71f9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302145"
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