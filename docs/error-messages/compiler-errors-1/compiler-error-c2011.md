---
title: "編譯器錯誤 C2011 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2011
dev_langs: C++
helpviewer_keywords: C2011
ms.assetid: 992c9d51-e850-4d53-b86b-02e73b38249c
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c599d6add1fa51c6aae7f04019eacdc94f11bb15
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2011"></a>編譯器錯誤 C2011
'identifier': 'type' 類型重複定義  
  
 識別項已定義為 `type`。 檢查識別項是否重複定義。  
  
 如果您將標頭檔或類型庫多次匯入至相同檔案中，您也會收到 C2011。 若要防止多次包含標頭檔中定義的類型，使用 include 防護或`#pragma`[一旦](../../preprocessor/once.md)指示詞的標頭檔中。  
  
 如果您需要尋找重複定義類型的初始宣告，您可以使用[/P](../../build/reference/p-preprocess-to-a-file.md)產生前置處理過的輸出的編譯器旗標傳遞給編譯器。 您可以使用文字搜尋工具，在輸出檔中尋找重複定義的識別項的執行個體。  
  
 下列範例會產生 C2011，並示範修正此問題的方法：  
  
```  
// C2011.cpp  
// compile with: /c  
struct S;  
union S;   // C2011  
union S2;   // OK  
```