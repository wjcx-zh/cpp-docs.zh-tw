---
title: 型別轉換的 MFC 類別物件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.classes
dev_langs:
- C++
helpviewer_keywords:
- macros [MFC], type casting
- pointers [MFC], type casting
- type casts [MFC]
- casting types [MFC]
- macros [MFC], casting pointers
ms.assetid: e138465e-c35f-4e84-b788-bd200ccf2f0e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2d90b188b99f4f0711635cc47c03383617b9046e
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37886007"
---
# <a name="type-casting-of-mfc-class-objects"></a>MFC 類別物件的類型轉換
類型轉型的巨集可用來指向特定的類別，使用或不檢查轉換合法的物件指標的指定的指標轉型。  
  
 下表列出 MFC 類型轉型的巨集。  
  
### <a name="macros-that-cast-pointers-to-mfc-class-objects"></a>轉型 MFC 類別物件的指標的巨集  
  
|||  
|-|-|  
|[DYNAMIC_DOWNCAST](#dynamic_downcast)|檢查是否為合法轉換時，會轉換類別物件的指標的指標。|  
|[STATIC_DOWNCAST](#static_downcast)|轉換成物件的指標，從一個類別的指標相關的型別。 在偵錯組建中，如果會造成判斷提示的物件不是"的 「 目標型別。|  
  
##  <a name="dynamic_downcast"></a>  DYNAMIC_DOWNCAST  
 提供一個便利的方式，來檢查是否為合法轉換時的類別物件的指標的指標轉型。  
  
```   
DYNAMIC_DOWNCAST(class, pointer)  
```  
  
### <a name="parameters"></a>參數  
 *class*  
 類別的名稱。  
  
 *pointer*  
 要轉換成的型別物件的指標的指標*類別*。  
  
### <a name="remarks"></a>備註  
 巨集將會轉換*指標*參數的物件指標*類別*參數的型別。  
  
 如果指標所參考的物件是 「 種類 」 已識別的類別，此巨集會傳回適當的指標。 如果不是合法的轉換，巨集就會傳回 NULL。  
  
##  <a name="static_downcast"></a>  STATIC_DOWNCAST  
 轉型*pobject*指標*class_name*物件。  
  
```   
STATIC_DOWNCAST(class_name, pobject)   
```  
  
### <a name="parameters"></a>參數  
 *class_name*  
 要轉換成的類別名稱。  
  
 *pobject*  
 要轉換成指標的指標*class_name*物件。  
  
### <a name="remarks"></a>備註  
 *pobject*必須是 NULL，或指向物件的類別衍生，直接或間接從*class_name*。 在您的應用程式，以定義 _DEBUG 前置處理器符號的組建中，如果，將 ASSERT 巨集*pobject*不是 NULL，或如果它指向的物件不是 「 種類 」 中指定的類別*class_name*參數 (請參閱[cobject:: Iskindof](../../mfc/reference/cobject-class.md#iskindof))。 在非 **_DEBUG**巨集的組建執行不含任何類型檢查的轉換。  
  
 中指定的類別*class_name*參數必須衍生自`CObject`，而且必須使用 DECLARE_DYNAMIC 和您的類別、 DECLARE_DYNCREATE IMPLEMENT_DYNCREATE，或 DECLARE_SERIAL 和 IMPLEMENT_一文中所述的序列的巨集，也[CObject 類別： 從 CObject 衍生類別](../../mfc/deriving-a-class-from-cobject.md)。  
  
 例如，您可能會轉型的指標`CMyDoc`，稱為`pMyDoc`，指標`CDocument`使用下列運算式：  
  
 [!code-cpp[NVC_MFCDocView#197](../../mfc/codesnippet/cpp/type-casting-of-mfc-class-objects_1.cpp)]  
  
 如果`pMyDoc`未指向物件直接或間接衍生自`CDocument`，會判斷提示巨集。  
  
## <a name="see-also"></a>另請參閱  
 [巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
