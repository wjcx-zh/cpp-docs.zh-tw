---
title: 編譯器錯誤 C3295 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3295
dev_langs:
- C++
helpviewer_keywords:
- C3295
ms.assetid: 83f0aa4d-0e0a-4905-9f66-fcf9991fc07a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 25fd1a04e0be46943b4fd183b470b369f810a0d1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33253953"
---
# <a name="compiler-error-c3295"></a>編譯器錯誤 C3295
'#pragma pragma' 只能使用在全域或命名空間範圍  
  
 有些 pragma 無法用於函式中。  請參閱[Pragma 指示詞和 __Pragma 關鍵字](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)如需詳細資訊。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3295。  
  
```  
// C3295.cpp  
int main() {  
   #pragma managed   // C3295  
}  
```