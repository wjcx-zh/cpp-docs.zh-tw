---
title: "輸入的 MFC 類別物件轉型 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.classes
dev_langs:
- C++
helpviewer_keywords:
- macros, type casting
- pointers, type casting
- type casts
- casting types
- macros, casting pointers
ms.assetid: e138465e-c35f-4e84-b788-bd200ccf2f0e
caps.latest.revision: 15
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: f1ae094e7085017f03daab3f73323da13ab1be39
ms.lasthandoff: 02/24/2017

---
# <a name="type-casting-of-mfc-class-objects"></a>MFC 類別物件的類型轉換
類型轉換的巨集提供指向包含或不含檢查轉型合法的特定類別的物件指標的指定的指標轉型的方法。  
  
 下表列出 MFC 類型轉換的巨集。  
  
### <a name="macros-that-cast-pointers-to-mfc-class-objects"></a>MFC 類別物件的指標轉型的巨集  
  
|||  
|-|-|  
|[DYNAMIC_DOWNCAST](#dynamic_downcast)|檢查是否為合法轉換時，會轉換類別物件的指標的指標。|  
|[STATIC_DOWNCAST](#static_downcast)|從一種相關類型的指標類別會轉換成物件的指標。 在偵錯組建中，會導致**ASSERT**如果物件不是 」 的 「 目標型別。|  
  
##  <a name="a-namedynamicdowncasta--dynamicdowncast"></a><a name="dynamic_downcast"></a>DYNAMIC_DOWNCAST  
 提供便利的類別物件的指標的指標轉型檢查是否為合法的轉型時。  
  
```   
DYNAMIC_DOWNCAST(class, pointer)  
```  
  
### <a name="parameters"></a>參數  
 `class`  
 類別名稱。  
  
 `pointer`  
 轉換類型的物件指標的指標`class`。  
  
### <a name="remarks"></a>備註  
 轉換巨集將`pointer`參數的物件指標`class`參數的型別。  
  
 如果指標所參考的物件 」 的 「 識別的類別，此巨集會傳回適當的指標。 如果不是合法的轉換，巨集會傳回**NULL**。  
  
##  <a name="a-namestaticdowncasta--staticdowncast"></a><a name="static_downcast"></a>STATIC_DOWNCAST  
 轉換 （cast) *pobject*指標*class_name*物件。  
  
```   
STATIC_DOWNCAST(class_name, pobject)   
```  
  
### <a name="parameters"></a>參數  
 *class_name*  
 轉換成類別的名稱。  
  
 *pobject*  
 要轉換成指標的指標*class_name*物件。  
  
### <a name="remarks"></a>備註  
 *pobject*必須是**NULL**，或指向物件的類別衍生，直接或間接從*class_name*。 在您的應用程式的組建**_DEBUG**前置處理器符號定義之後，巨集會將**ASSERT**如果*pobject*不是**NULL**，或如果指向的物件不是 「 種類 」 中指定的類別*class_name*參數 (請參閱[cobject:: Iskindof](../../mfc/reference/cobject-class.md#iskindof))。 在非**_DEBUG**巨集的組建執行轉型，而不需要任何型別檢查。  
  
 中指定的類別*class_name*參數必須衍生自`CObject`，而且必須使用`DECLARE_DYNAMIC`和`IMPLEMENT_DYNAMIC`、`DECLARE_DYNCREATE`和`IMPLEMENT_DYNCREATE`，或`DECLARE_SERIAL`和`IMPLEMENT_SERIAL`巨集文件中所述[CObject 類別︰ 衍生自 CObject 的類別](../../mfc/deriving-a-class-from-cobject.md)。  
  
 例如，您可能會將指標轉換為`CMyDoc`，稱為`pMyDoc`，與指標**CDocument**使用下列運算式︰  
  
 [!code-cpp[NVC_MFCDocView #&197;](../../mfc/codesnippet/cpp/type-casting-of-mfc-class-objects_1.cpp)]  
  
 如果`pMyDoc`不指向物件直接或間接衍生自**CDocument**，巨集會將**ASSERT**。  
  
## <a name="see-also"></a>另請參閱  
 [巨集和全域變數](../../mfc/reference/mfc-macros-and-globals.md)

