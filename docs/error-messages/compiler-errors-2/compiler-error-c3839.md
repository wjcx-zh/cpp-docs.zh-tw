---
title: 編譯器錯誤 C3839 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3839
dev_langs:
- C++
helpviewer_keywords:
- C3839
ms.assetid: 0957faff-1e9f-439b-876b-85bd8d2c578d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cbb5541e07d168df36bae83f81b7b8a8a7273665
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269510"
---
# <a name="compiler-error-c3839"></a>編譯器錯誤 C3839
無法變更 managed 或 WinRT 類型中的對齊  
  
 變數的對齊方式在 managed 或 Windows 執行階段類型由 CLR 或 Windows 執行階段所控制，而且無法修改與[對齊](../../cpp/align-cpp.md)。  
  
 下列範例會產生 C3839：  
  
```  
// C3839a.cpp  
// compile with: /clr  
ref class C  
{  
public:  
   __declspec(align(32)) int m_j; // C3839  
};  
  
int main()  
{  
}  
```