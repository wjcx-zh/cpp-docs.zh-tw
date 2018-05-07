---
title: 編譯器警告 （層級 4） C4235 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4235
dev_langs:
- C++
helpviewer_keywords:
- C4235
ms.assetid: d4214799-d62c-4674-b4e2-9e201c303303
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc63640bc58caefa281b9207b9796ffdf387a7a8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4235"></a>編譯器警告 (層級 4) C4235
使用非標準擴充: 'keyword' 關鍵字不支援這種架構  
  
 編譯器不支援您使用的關鍵字。  
  
 這個警告會自動升級為錯誤。 如果您想要修改此行為，使用[#pragma 警告](../../preprocessor/warning.md)。 例如，若要將層級 2 警告 c4235，使用下列程式碼  
  
```  
#pragma warning(2:4235)  
```  
  
 在您的原始程式碼檔。