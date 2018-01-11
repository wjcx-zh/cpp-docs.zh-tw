---
title: "norm 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- norm
- AMP_SHORT_VECTORS/norm
- AMP_SHORT_VECTORS/Concurrency::graphics::norm Constructor
dev_langs: C++
ms.assetid: 73002f3d-c25e-4119-bcd3-4c46c9b6abf1
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 785c214ed904d1591c5d532ec9f09d42c93dc2ca
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="norm-class"></a>norm 類別
表示範數字。 每個項目是浮點數中的範圍 [-1.0 f、 1.0 f]。  
  
## <a name="syntax"></a>語法  
  
```  
class norm;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[norm 建構函式](#ctor)|多載。 預設建構函式。 將初始化為 0.0。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|norm::operator-||  
|norm::operator-||  
|norm::operator float|轉換運算子。 將範數字轉換成浮點值。|  
|norm::operator * =||  
|norm::operator / =||  
|norm::operator + +||  
|norm::operator + =||  
|norm::operator =||  
|norm::operator =||  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `norm`  
  
## <a name="requirements"></a>需求  
 **標頭：** amp_short_vectors.h  
  
 **命名空間：** concurrency:: graphics  
  
##  <a name="ctor"></a>norm 

 預設建構函式。 將初始化為 0.0。  
  
```  
norm(
    void) restrict(amp,
    cpu);

 
explicit norm(
    float _V) restrict(amp,
    cpu);

 
explicit norm(
    unsigned int _V) restrict(amp,
    cpu);

 
explicit norm(
    int _V) restrict(amp,
    cpu);

 
explicit norm(
    double _V) restrict(amp,
    cpu);

 
norm(
    const norm& _Other) restrict(amp,
    cpu);

 
norm(
    const unorm& _Other) restrict(amp,
    cpu);
```  
  
### <a name="parameters"></a>參數  
 `_V`  
 用來初始化的值。  
  
 `_Other`  
 用來初始化物件。  
  
## <a name="see-also"></a>請參閱  
 [Concurrency::graphics 命名空間](concurrency-graphics-namespace.md)
