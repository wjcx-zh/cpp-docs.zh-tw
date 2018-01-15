---
title: "_ATL_FUNC_INFO 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _ATL_FUNC_INFO
- ATL::_ATL_FUNC_INFO
- ATL._ATL_FUNC_INFO
dev_langs: C++
helpviewer_keywords:
- _ATL_FUNC_INFO structure
- ATL_FUNC_INFO structure
ms.assetid: 441ebe2c-f971-47de-9f52-a258e8d6f88e
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b1bbff1fa040454fc8288053938bb439d505b461
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="atlfuncinfo-structure"></a>_ATL_FUNC_INFO 結構
包含用來描述上的分配介面的方法或屬性的型別資訊。  
  
## <a name="syntax"></a>語法  
  
```
struct _ATL_FUNC_INFO {
    CALLCONV cc;
    VARTYPE vtReturn;
    SHORT nParams;
    VARTYPE pVarTypes[_ATL_MAX_VARTYPES];
};
```  
  
## <a name="members"></a>成員  
 **[副本]**  
 呼叫慣例。 當使用這個結構[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)類別，這個成員必須是**CC_STDCALL**。 `CC_CDECL`是唯一的選項中為 Windows CE 支援`CALLCONV`欄位`_ATL_FUNC_INFO`結構。 不支援的任何其他值，因此其行為未定義。  
  
 **vtReturn**  
 Variant 類型函式的傳回值。  
  
 **nParams**  
 函式的參數數目。  
  
 **pVarTypes**  
 陣列的變異數的函式參數的類型。  
  
## <a name="remarks"></a>備註  
 就內部而言，ATL 會使用此結構來保存從類型程式庫取得的資訊。 您可能需要直接操作此結構，如果您提供型別搭配使用的事件處理常式資訊[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)類別和[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)巨集。  
  
## <a name="example"></a>範例  
 指定 IDL 中定義的分配介面方法：  
  
 [!code-cpp[NVC_ATL_Windowing#139](../../atl/codesnippet/cpp/atl-func-info-structure_1.idl)]  
  
 您要定義`_ATL_FUNC_INFO`結構：  
  
 [!code-cpp[NVC_ATL_Windowing#140](../../atl/codesnippet/cpp/atl-func-info-structure_2.h)]  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  
  
## <a name="see-also"></a>請參閱  
 [結構](../../atl/reference/atl-structures.md)   
 [IDispEventSimpleImpl 類別](../../atl/reference/idispeventsimpleimpl-class.md)   
 [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)





