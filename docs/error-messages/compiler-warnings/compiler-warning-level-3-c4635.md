---
title: 編譯器警告 （層級 3） C4635 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4635
dev_langs:
- C++
helpviewer_keywords:
- C4635
ms.assetid: b2ba90de-c093-4a76-8076-b65878467574
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2dcc4b7466ed53a187b7f34ec45084a94adb59b4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33291768"
---
# <a name="compiler-warning-level-3-c4635"></a>編譯器警告 (層級 3) C4635
XML 文件註解目標: XML 格式錯誤: 原因  
  
 編譯器發現 XML 標記有一些問題。  請修正問題並重新編譯。  
  
 下列範例會產生 C4635：  
  
```  
// C4635.cpp  
// compile with: /doc /clr /W3 /c  
/// <summary>     
/// The contents of the folder have changed.  
/// <summary/>   // C4635  
  
// try the following line instead  
// /// </summary>  
public ref class Test {};  
```  
  
 請注意，這個範例的輸出顯示： **結束標記 'member' 與起始標籤 'summary' 不對稱。**  
  
 此範例的問題是結束標記\<摘要 > 格式不正確，但編譯器無法辨識為\<摘要 > 結束標記。  \<成員 > 標記內嵌於.xdc 檔編譯器在每個 /doc 編譯中。  因此，此處的問題在於結束標記\</member >，不符合之前編譯器處理過的起始標記 (\<摘要 >。