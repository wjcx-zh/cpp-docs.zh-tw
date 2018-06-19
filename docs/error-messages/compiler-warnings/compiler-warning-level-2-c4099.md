---
title: 編譯器警告 （層級 2） C4099 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4099
dev_langs:
- C++
helpviewer_keywords:
- C4099
ms.assetid: 00bb803d-cae7-4ab8-8969-b46f54139ac8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: afecb3fb2420d27bedf16c81894f224a1119a67b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33309464"
---
# <a name="compiler-warning-level-2-c4099"></a>編譯器警告 (層級 2) C4099
'identifier': 第一個看到使用 'objecttype1' 現在發現使用 'objecttype2' 的型別名稱  
  
 結構宣告的物件定義為類別，或宣告為類別的物件定義為結構。 編譯器會使用定義中提供的類型。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4099。  
  
```  
// C4099.cpp  
// compile with: /W2 /c  
struct A;  
class A {};   // C4099, use different identifer or use same object type  
```