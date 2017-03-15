---
title: "_ATL_FUNC_INFO 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _ATL_FUNC_INFO
- ATL::_ATL_FUNC_INFO
- ATL._ATL_FUNC_INFO
dev_langs:
- C++
helpviewer_keywords:
- _ATL_FUNC_INFO structure
- ATL_FUNC_INFO structure
ms.assetid: 441ebe2c-f971-47de-9f52-a258e8d6f88e
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
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
translationtype: Machine Translation
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: c18e1c5a41ef910cfe327fdbdd8d8885ef30a092
ms.lasthandoff: 02/24/2017

---
# <a name="atlfuncinfo-structure"></a>_ATL_FUNC_INFO 結構
包含用來描述分配介面上的方法或屬性的型別資訊。  
  
## <a name="syntax"></a>語法  
  
```
struct _ATL_FUNC_INFO {
    CALLCONV cc;
    VARTYPE vtReturn;
    SHORT nParams;
    VARTYPE pVarTypes[_ATL_MAX_VARTYPES];
};
```  
  
## <a name="members"></a>Members  
 **收件者**  
 呼叫慣例。 當使用這個結構[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)類別，這個成員必須是**CC_STDCALL**。 `CC_CDECL`是唯一的選項中的 Windows CE 支援`CALLCONV`欄位`_ATL_FUNC_INFO`結構。 不支援的任何其他值，因此其行為未定義。  
  
 **vtReturn**  
 Variant 類型函式的傳回值。  
  
 **nParams**  
 函式參數的數目。  
  
 **pVarTypes**  
 陣列的變異數的函式參數的類型。  
  
## <a name="remarks"></a>備註  
 就內部而言，ATL 會使用此結構來容納從型別程式庫取得的資訊。 您可能需要直接操作此結構，如果您提供事件處理常式搭配使用的型別資訊[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)類別和[SINK_ENTRY_INFO](http://msdn.microsoft.com/library/1a0ae260-2c82-4926-a537-db01e5f206a7)巨集。  
  
## <a name="example"></a>範例  
 指定 IDL 中定義的分配介面方法︰  
  
 [!code-cpp[NVC_ATL_Windowing #&139;](../../atl/codesnippet/cpp/atl-func-info-structure_1.idl)]  
  
 您會定義`_ATL_FUNC_INFO`結構︰  
  
 [!code-cpp[NVC_ATL_Windowing #&140;](../../atl/codesnippet/cpp/atl-func-info-structure_2.h)]  
  
## <a name="requirements"></a>需求  
 **標頭︰**於 atlcom.h  
  
## <a name="see-also"></a>另請參閱  
 [結構](../../atl/reference/atl-structures.md)   
 [IDispEventSimpleImpl 類別](../../atl/reference/idispeventsimpleimpl-class.md)   
 [SINK_ENTRY_INFO](http://msdn.microsoft.com/library/1a0ae260-2c82-4926-a537-db01e5f206a7)






