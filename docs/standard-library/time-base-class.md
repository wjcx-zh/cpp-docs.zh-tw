---
title: "time_base 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- time_base
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
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: 86e27eec232094c1e57120f6f811c96b4e4a4871
ms.contentlocale: zh-tw
ms.lasthandoff: 04/19/2017

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




