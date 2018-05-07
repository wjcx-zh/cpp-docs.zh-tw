---
title: 編譯器警告 （層級 3） C4192 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4192
dev_langs:
- C++
helpviewer_keywords:
- C4192
ms.assetid: ea5f91fa-8c96-4f3f-ac42-0c8a86d4e5df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3bae9b7af95de94b8f667cb09710af21044f8b80
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4192"></a>編譯器警告 （層級 3） C4192
會自動匯入類型程式庫 'library' 時排除 'name'  
  
 A`#import`程式庫包含的項目，*名稱*，也就是也在 Win32 系統標頭中定義。 類型程式庫的限制，因為名稱例如**IUnknown**或 GUID 通常會定義在型別程式庫複製系統標頭的定義。 `#import` 會偵測到這些項目，並拒絕將它們併入.tlh 和.tli 標頭檔中。  
  
 若要覆寫此行為，請使用`#import`屬性[no_auto_exclude](../../preprocessor/no-auto-exclude.md)和[include （)](../../preprocessor/include-parens.md)。