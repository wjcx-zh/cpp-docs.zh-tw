---
title: 編譯器錯誤 C2870 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2870
dev_langs:
- C++
helpviewer_keywords:
- C2870
ms.assetid: 80523ee9-1fd3-4dc4-8a77-5083deb99066
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5fe9f47a96422493d6d731a18add8c23ff683f14
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33243485"
---
# <a name="compiler-error-c2870"></a>編譯器錯誤 C2870
'name': 命名空間定義必須出現在檔案範圍，或立即在其他命名空間定義  
  
 定義命名空間`name`不正確。 命名空間必須定義在檔案範圍 （之外的所有區塊和類別） 或立即在另一個命名空間。  
  
 下列範例會產生 C2870:  
  
```  
// C2870.cpp  
// compile with: /c  
int main() {  
   namespace A { int i; };   // C2870  
}  
```