---
title: '&lt;ccomplex&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <ccomplex>
dev_langs:
- C++
ms.assetid: a9fcb5f0-88e3-464b-a5fd-d1afb8cd7e6f
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: 63374ad7a56060da78621e9543f38dcfe8a06ae7
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="ltccomplexgt"></a>&lt;ccomplex&gt;
包括 C++ 標準程式庫標頭 [\<complex>](../standard-library/complex.md)，它會有效率地包括標準 C 程式庫標頭 \<complex.h>，並將相關聯的名稱新增至 `std` 命名空間。  
  
## <a name="syntax"></a>語法  
  
```cpp  
#include <ccomplex>  
  
```  
  
## <a name="remarks"></a>備註  
 包含此標頭可保證，透過使用 Standard C 程式庫標頭中的外部連結所宣告的名稱會在 `std` 命名空間中宣告。  
  
 名稱 `clog` (宣告於 \<complex.h> 中) 未定義在 `std` 命名空間中，因為可能發生與 `clog` (宣告於 [\<iostream>](../standard-library/iostream.md) 中) 的衝突。  
  
## <a name="see-also"></a>另請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C++ 標準程式庫概觀](../standard-library/cpp-standard-library-overview.md)




