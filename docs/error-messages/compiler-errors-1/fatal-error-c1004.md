---
title: "嚴重錯誤 C1004 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1004
dev_langs: C++
helpviewer_keywords: C1004
ms.assetid: dbe034b0-6eb0-41b4-a50c-2fccf9e78ad4
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c6a9e74d7918e1cb2c9190c87f4f1ec75f89237b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1004"></a>嚴重錯誤 C1004
找到未預期的檔案結尾  
  
 編譯器遇到來源檔案的結尾，而不會解決建構。 程式碼可能會遺漏下列項目之一：  
  
-   右大括號  
  
-   右括號  
  
-   結束的註解標記 (* /)  
  
-   分號  
  
 若要解決這個錯誤，請檢查下列：  
  
-   預設磁碟機空間不足的暫存檔案，需要更多關於倍的空間與原始程式檔案。  
  
-   `#if`指示詞會評估為 false 缺少右`#endif`指示詞。  
  
-   原始程式檔未以歸位字元和換行字元結尾。  
  
 下列範例會產生 C1004:  
  
```  
// C1004.cpp  
#if TEST  
int main() {}  
// C1004  
```  
  
 可能的解決方式：  
  
```  
// C1004b.cpp  
#if TEST  
#endif  
  
int main() {}  
```