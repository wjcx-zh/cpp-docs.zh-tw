---
title: 編譯器錯誤 C2569 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2569
dev_langs:
- C++
helpviewer_keywords:
- C2569
ms.assetid: 092bed1e-f631-436c-9586-7750629f6fac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4869f13d972cea80bd590633b3aae2ea0c96f392
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33230338"
---
# <a name="compiler-error-c2569"></a>編譯器錯誤 C2569
'EnumOrUnion': 列舉/等位不能當做基底類別  
  
 如果您必須是型別衍生自指定的等位或列舉型別，變更等位或列舉類別或結構。  
  
 下列範例會產生 C2569:  
  
```  
// C2569.cpp  
// compile with: /c  
union ubase {};  
class cHasPubUBase : public ubase {};   // C2569  
// OK  
struct sbase {};  
class cHasPubUBase : public sbase {};  
```