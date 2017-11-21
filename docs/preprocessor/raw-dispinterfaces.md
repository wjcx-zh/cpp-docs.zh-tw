---
title: "raw_dispinterfaces |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: raw_dispinterfaces
dev_langs: C++
helpviewer_keywords: raw_dispinterfaces attribute
ms.assetid: f762864d-29bf-445b-825a-ba7b29a95409
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c73a30779bf85e39ca97d0e6f4979c070de4e00c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="rawdispinterfaces"></a>raw_dispinterfaces
**C + + 特定的**  
  
 告知編譯器產生低階包裝函式呼叫的分配介面方法和屬性**idispatch:: Invoke**並傳回`HRESULT`錯誤碼。  
  
## <a name="syntax"></a>語法  
  
```  
raw_dispinterfaces  
```  
  
## <a name="remarks"></a>備註  
 如果沒有指定此屬性，只會產生高階包裝函式，一旦失敗就會擲回 C++ 例外狀況。  
  
 **END c + + 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [#import 指示詞](../preprocessor/hash-import-directive-cpp.md)