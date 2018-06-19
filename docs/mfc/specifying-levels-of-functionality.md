---
title: 指定功能層級 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CObject class [MFC], adding functionality to derived classes
- runtime [MFC], class information
- serialization [MFC], Cobject
- dynamic creation support
- levels [MFC], functionality in CObject
- run-time class [MFC], information support
- levels [MFC]
ms.assetid: 562669ba-c858-4f66-b5f1-b3beeea4f486
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f32b9502d2e8bd1c1483d817b759ca204f5c9c1a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33381143"
---
# <a name="specifying-levels-of-functionality"></a>指定功能層級
本文說明如何新增下列層級的功能以您[CObject](../mfc/reference/cobject-class.md)-衍生的類別：  
  
-   [執行階段類別資訊](#_core_to_add_run.2d.time_class_information)  
  
-   [動態建立支援](#_core_to_add_dynamic_creation_support)  
  
-   [序列化支援](#_core_to_add_serialization_support)  
  
 如需一般的說明`CObject`功能，請參閱文章[從 CObject 衍生類別](../mfc/deriving-a-class-from-cobject.md)。  
  
-   [執行階段類別資訊](#_core_to_add_run.2d.time_class_information)  
#### <a name="_core_to_add_run.2d.time_class_information"></a> 若要加入執行階段類別資訊  
  
1.  衍生您的類別從`CObject`中所述，[從 CObject 衍生類別](../mfc/deriving-a-class-from-cobject.md)發行項。  
  
2.  使用`DECLARE_DYNAMIC`巨集，在您類別的宣告，如下所示：  
  
     [!code-cpp[NVC_MFCCObjectSample#2](../mfc/codesnippet/cpp/specifying-levels-of-functionality_1.h)]  
  
3.  使用`IMPLEMENT_DYNAMIC`巨集在實作檔 (。CPP) 您的類別。 這個巨集接受做為引數的類別和其基底類別名稱，如下所示：  
  
     [!code-cpp[NVC_MFCCObjectSample#3](../mfc/codesnippet/cpp/specifying-levels-of-functionality_2.cpp)]  
  
> [!NOTE]
>  一律將`IMPLEMENT_DYNAMIC`在實作檔 (。CPP) 為您的類別。 `IMPLEMENT_DYNAMIC`巨集應該只評估一次在編譯期間，因此不應在介面檔案 (。H），可能無法包含在多個檔案。  
  
#### <a name="_core_to_add_dynamic_creation_support"></a> 若要加入動態建立支援  
  
1.  衍生您的類別從`CObject`。  
  
2.  使用`DECLARE_DYNCREATE`類別宣告中的巨集。  
  
3.  定義沒有引數 （預設建構函式） 的建構函式。  
  
4.  使用`IMPLEMENT_DYNCREATE`類別實作檔中的巨集。  
  
#### <a name="_core_to_add_serialization_support"></a> 若要加入序列化支援  
  
1.  衍生您的類別從`CObject`。  
  
2.  覆寫`Serialize`成員函式。  
  
    > [!NOTE]
    >  如果您呼叫`Serialize`直接，也就是您不希望將序列化的物件，透過多型的指標，請略過步驟 3 到 5。  
  
3.  使用`DECLARE_SERIAL`類別宣告中的巨集。  
  
4.  定義沒有引數 （預設建構函式） 的建構函式。  
  
5.  使用`IMPLEMENT_SERIAL`類別實作檔中的巨集。  
  
> [!NOTE]
>  「 多型的指標 」 指向類別的物件 (它呼叫的) 或衍生自 （比方說，B） 的任何類別的物件。 若要序列化多型的指標透過，架構必須判斷執行階段類別，它會序列化 (B)，因為它可能是衍生自一些基底類別 (A) 的任何類別物件的物件。  
  
 如需有關如何啟用序列化，當您衍生您的類別從`CObject`，請參閱文章[MFC 中的檔案](../mfc/files-in-mfc.md)和[序列化](../mfc/serialization-in-mfc.md)。  
  
## <a name="see-also"></a>另請參閱  
 [從 CObject 衍生類別](../mfc/deriving-a-class-from-cobject.md)
