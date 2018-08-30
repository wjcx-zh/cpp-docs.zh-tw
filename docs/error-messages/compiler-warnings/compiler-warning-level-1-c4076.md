---
title: 編譯器警告 （層級 1） C4076 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4076
dev_langs:
- C++
helpviewer_keywords:
- C4076
ms.assetid: 04581066-313a-4a11-bb60-721e6d038d75
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 928b0a78c09773e334c1a291877b74304dab66ec
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43198474"
---
# <a name="compiler-warning-level-1-c4076"></a>編譯器警告 (層級 1) C4076

> '*型別修飾詞*': 不可以搭配類型'*typename*'

## <a name="remarks"></a>備註

型別修飾詞，它是否**簽署**或是**不帶正負號**，不能與非整數類型。 *類型修飾詞*會被忽略。
  
## <a name="example"></a>範例  

下列範例會產生 C4076;若要修正此問題，請移除**不帶正負號**型別修飾詞：

```cpp
// C4076.cpp  
// compile with: /W1 /LD  
unsigned double x;   // C4076  
```