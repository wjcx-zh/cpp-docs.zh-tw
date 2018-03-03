---
title: "編譯器警告 （層級 3） C4192 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4192
dev_langs:
- C++
helpviewer_keywords:
- C4192
ms.assetid: ea5f91fa-8c96-4f3f-ac42-0c8a86d4e5df
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 022c0e0aac8d231963ddf6d5d3715d55f726a8b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4192"></a>編譯器警告 （層級 3） C4192
會自動匯入類型程式庫 'library' 時排除 'name'  
  
 A`#import`程式庫包含的項目，*名稱*，也就是也在 Win32 系統標頭中定義。 類型程式庫的限制，因為名稱例如**IUnknown**或 GUID 通常會定義在型別程式庫複製系統標頭的定義。 `#import`會偵測到這些項目，並拒絕將它們併入.tlh 和.tli 標頭檔中。  
  
 若要覆寫此行為，請使用`#import`屬性[no_auto_exclude](../../preprocessor/no-auto-exclude.md)和[include （)](../../preprocessor/include-parens.md)。