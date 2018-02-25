---
title: "is_error_code_enum 結構 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- future/std::is_error_code_enum
dev_langs:
- C++
ms.assetid: 84ae4b99-66d2-41ba-9b50-645fcbe14630
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 912b21f97cdbc05bc33122f93f22e13185e52e09
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="iserrorcodeenum-structure"></a>is_error_code_enum 結構
指出 [future_errc](../standard-library/future-enums.md#future_errc) 適合儲存 [error_code](../standard-library/error-code-class.md) 的特製化。  
  
## <a name="syntax"></a>語法  
  
```
template <>
struct is_error_code_enum<Future_errc> : public true_type;
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<未來 >  
  
 **命名空間：** std  
  
## <a name="see-also"></a>請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\<future>](../standard-library/future.md)



