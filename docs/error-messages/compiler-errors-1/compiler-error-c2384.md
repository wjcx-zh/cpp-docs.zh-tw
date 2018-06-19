---
title: 編譯器錯誤 C2384 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2384
dev_langs:
- C++
helpviewer_keywords:
- C2384
ms.assetid: 8145f7ad-31b1-406d-ac43-0d557feab635
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce139166e2378a26a91bc66db134ec6098aedbdc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33194927"
---
# <a name="compiler-error-c2384"></a>編譯器錯誤 C2384
'member'：無法將 __declspec(thread) 套用至 Managed 或 WinRT 類別的成員  
  
 [執行緒](../../cpp/thread.md)`__declspec`修飾詞不能在 managed 成員或 Windows 執行階段類別。  
  
 Managed 程式碼中的靜態執行緒區域儲存區僅可以使用於以靜態方式載入的 DLL — 在處理序啟動時 DLL 必須以靜態方式載入。 Windows 執行階段不支援執行緒區域儲存區。  
  
 下列範例會產生 C2384，並示範如何在 C++/CLI 程式碼中修正此問題：  
  
```  
// C2384.cpp  
// compile with: /clr /c  
public ref class B {  
public:  
   __declspec( thread ) static int tls_i = 1;   // C2384  
  
   // OK - declare with attribute instead  
   [System::ThreadStaticAttribute]  
   static int tls_j;  
};  
```