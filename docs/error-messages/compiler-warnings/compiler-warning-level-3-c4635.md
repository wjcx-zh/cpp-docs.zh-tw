---
title: "編譯器警告 （層級 3） C4635 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4635
dev_langs: C++
helpviewer_keywords: C4635
ms.assetid: b2ba90de-c093-4a76-8076-b65878467574
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 16b6a19618afeed952cfa594961a0e4ccb777d26
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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