---
title: "編譯器錯誤 C2891 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2891
dev_langs: C++
helpviewer_keywords: C2891
ms.assetid: e12cfb2d-df45-4b0d-b155-c51d17e812fa
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6c35294472fe4142e7e6689adfc5f5f71c27b664
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2891"></a>編譯器錯誤 C2891
'parameter': 無法取得樣板參數的位址  
  
 您無法取得樣板參數的位址，除非它是左值。 型別參數不是左值，因為它們沒有位址。 都不是左值的範本參數清單中的非類型值也不會有位址。 這是造成編譯器錯誤 C2891，程式碼範例，因為傳遞做為範本參數的值是編譯器產生的複製的樣板引數。  
  
```  
template <int i> int* f() { return &i; }  
```  
  
 都是左值，例如參考類型的樣板參數可以有其取得位址。  
  
```  
template <int& r> int* f() { return &r; }  
```  
  
 若要更正這個錯誤，不會樣板參數的位址除非它是左值。