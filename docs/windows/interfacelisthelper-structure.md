---
title: "InterfaceListHelper 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::InterfaceListHelper
dev_langs: C++
helpviewer_keywords: InterfaceListHelper structure
ms.assetid: 4297e419-c96b-45df-8a00-7568062125ba
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4465a380d24cbb9607785e958a88801c5de68b15
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="interfacelisthelper-structure"></a>InterfaceListHelper 結構
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
template <  
   typename T0,  
   typename T1 = Nil,  
   typename T2 = Nil,  
   typename T3 = Nil,  
   typename T4 = Nil,  
   typename T5 = Nil,  
   typename T6 = Nil,  
   typename T7 = Nil,  
   typename T8 = Nil,  
   typename T9 = Nil  
>  
struct InterfaceListHelper;  
  
template <  
   typename T0  
>  
struct InterfaceListHelper<T0, Nil, Nil, Nil, Nil, Nil, Nil, Nil, Nil>;  
```  
  
#### <a name="parameters"></a>參數  
 `T0`  
 樣板參數 0，這是必要。  
  
 `T1`  
 樣板參數 1，其預設值是 未指定。  
  
 `T2`  
 樣板參數 2，其預設值是 未指定。第三個樣板參數。  
  
 `T3`  
 樣板參數 3，其預設值是 未指定。  
  
 `T4`  
 樣板參數 4，其預設值是 未指定。  
  
 `T5`  
 樣板參數 5，其預設值是 未指定。  
  
 `T6`  
 樣板參數 6，其預設值是 未指定。  
  
 `T7`  
 樣板參數 7，其預設值是 未指定。  
  
 `T8`  
 樣板參數 8，其預設值是 未指定。  
  
 `T9`  
 樣板參數 9，其預設值是 未指定。  
  
## <a name="remarks"></a>備註  
 InterfaceList 型別是以遞迴方式套用指定的範本參數引數。  
  
 InterfaceListHelper 範本使用的樣板參數`T0`定義的第一個資料成員 InterfaceList 結構，然後遞迴地 InterfaceListHelper 範本套用至任何剩餘的範本參數。 沒有剩餘的範本參數，就會停止 InterfaceListHelper。  
  
## <a name="members"></a>Members  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|說明|  
|----------|-----------------|  
|`TypeT`|InterfaceList 類型的同義字。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `InterfaceListHelper`  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)