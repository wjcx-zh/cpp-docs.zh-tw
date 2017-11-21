---
title: "once_flag 結構 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: mutex/std::once_flag
dev_langs: C++
ms.assetid: 71bfb88d-ca8c-4082-a6e1-ff52151e8629
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: dded28d846ded9472ff9cee140366e5bab18b49a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="onceflag-structure"></a>once_flag 結構
表示搭配樣板函式 [call_once](../standard-library/mutex-functions.md#call_once) 使用的 `struct`，以確保即使執行多個執行緒，該初始化程式碼僅會呼叫一次。  
  
## <a name="syntax"></a>語法  
  
struct once_flag { constexpr once_flag() noexcept; once_flag(const once_flag&); once_flag& operator=(const once_flag&); };  
  
## <a name="remarks"></a>備註  
 `once_flag` `struct`只有預設建構函式。  
  
 可以建立 `once_flag` 類型的物件，但無法複製它們。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<mutex >  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex>](../standard-library/mutex.md)



