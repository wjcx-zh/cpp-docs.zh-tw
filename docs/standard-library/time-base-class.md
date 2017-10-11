---
title: "time_base 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- locale/std::time_base
dev_langs:
- C++
helpviewer_keywords:
- time_base class
ms.assetid: 9ae37f0b-9a42-496e-9870-3d9b71bab8fb
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: c1c7c6c708087827c853234dcbd4519c79fba2bf
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

---
# <a name="timebase-class"></a>time_base 類別
此類別會當成基底類別提供給樣板類別 time_get 的 facet，僅定義列舉類型 **dateorder** 和此類型的數個常數。  
  
## <a name="syntax"></a>語法  
  
```
class time_base : public locale::facet {
public:
    enum dateorder {no_order,
    dmy,
 mdy,
    ymd,
 ydm};
    time_base(
 size_t _Refs = 0)
 ~time_base();

};
```  
  
## <a name="remarks"></a>備註  
 每個常數特性都會以不同的方式描述，來將日期元件排序。 這些常數如下：  
  
- **no_order** 不會指定特定順序。  
  
- **dmy** 指定該順序依序為日、月、年，如 2 日 12 月 1979 年。  
  
- **mdy** 指定該順序依序為月、日、年，如 12 月 2 日，1979 年。  
  
- **ymd** 指定該順序依序為年、月、日，如 1979/12/2。  
  
- **ydm** 指定該順序依序為年、日、月，如 1979：2 日 12 月。  
  
## <a name="requirements"></a>需求  
 **標頭︰**\<locale>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)




