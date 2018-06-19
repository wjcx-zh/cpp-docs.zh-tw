---
title: 編譯器警告 (層級 1) C4788 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4788
dev_langs:
- C++
helpviewer_keywords:
- C4788
ms.assetid: 47d75bda-f833-4bdd-93a0-a134df0cd303
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 19a43fb9d79c63637b2bff9a27661a9f848ef6dc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33284195"
---
# <a name="compiler-warning-level-1-c4788"></a>編譯器警告 (層級 1) C4788
'identifier': 識別項被截斷成 'number' 個字元  
  
 編譯器限制允許函式名稱的長度上限。 當編譯器產生 funclets EH/SEH 的程式碼時，它會形成 funclet 名稱的函式名稱前面加上一些文字，例如"__catch"，"\__unwind"，或另一個字串。  
  
 產生的 funclet 名稱可能太長，而且編譯器將會截斷，並產生 C4788。  
  
 若要解決這個警告，請縮短原始函式名稱。 如果函式的 c + + 樣板函式或方法，使用 typedef 名稱的組件。 例如:   
  
```  
C1<x, y, z<T>>::C2<a,b,c>::f  
```  
  
 可以被取代：  
  
```  
typedef C1<x, y, z<T>>::C2<a,b,c> new_class ;  
new_class::f  
```  
  
 這個警告只在 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 編譯器中才會發生。