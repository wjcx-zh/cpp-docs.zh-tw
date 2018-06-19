---
title: 從 CObject 衍生類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CObject
dev_langs:
- C++
helpviewer_keywords:
- DECLARE_DYNCREATE macro [MFC]
- DECLARE_SERIAL macro [MFC]
- macros [MFC], serialization
- serialization [MFC], macros
- DECLARE_DYNAMIC macro [MFC]
- derived classes [MFC], from CObject
- CObject class [MFC], deriving serializable classes
- CObject class [MFC], deriving from
ms.assetid: 5ea4ea41-08b5-4bd8-b247-c5de8c152a27
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2d0b629617c1592387f3f959996fd3e9837242ea
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349353"
---
# <a name="deriving-a-class-from-cobject"></a>從 CObject 衍生類別
這篇文章描述最小的步驟，自[CObject](../mfc/reference/cobject-class.md)。 其他`CObject`類別文章說明利用特定的所需的步驟`CObject`功能，例如序列化和診斷的偵錯支援。  
  
 中的討論`CObject`，常使用的術語 「 介面檔案 」 和 「 實作檔案 」。 介面檔案 (通常稱為標頭檔，或。H 檔案） 包含在類別宣告和使用類別時所需的任何其他資訊。 實作檔 （或。CPP 檔案） 包含的類別定義，以及實作類別成員函式的程式碼。 例如，對於類別，名為`CPerson`，您通常會建立名為 PERSON 介面檔案。H 與實作檔名為 PERSON。CPP。 不過，有些不會在應用程式之間共用的小型類別，可能會很容易結合介面和實作在單一。CPP 檔案。  
  
 衍生的類別時，您可以選擇從四個層級的功能`CObject`:  
  
-   基本功能： 不支援執行階段類別資訊或序列化，但包括診斷的記憶體管理。  
  
-   基本功能，以及支援執行階段類別資訊。  
  
-   基本功能，以及執行階段類別資訊和動態建立的支援。  
  
-   基本功能，以及執行階段類別資訊、 動態建立和序列化支援。  
  
 （其會將稍後會做為基底類別） 的重複使用而設計的類別應該至少包含執行階段類別支援和序列化支援，如果不需要在未來的序列化不預期。  
  
 您選擇的功能層級使用的宣告和衍生自類別的實作中特定的宣告和實作巨集`CObject`。  
  
 下表顯示用來支援序列化和執行階段資訊的巨集之間的關聯性。  
  
### <a name="macros-used-for-serialization-and-run-time-information"></a>用於序列化和執行階段資訊的巨集  
  
|使用巨集|Cobject:: Iskindof|CRuntimeClass::<br /><br /> CreateObject|CArchive::operator >><br /><br /> CArchive::operator <<|  
|----------------|-----------------------|--------------------------------------|-------------------------------------------------------|  
|基本`CObject`功能|否|否|否|  
|`DECLARE_DYNAMIC`|是|否|否|  
|`DECLARE_DYNCREATE`|是|是|否|  
|`DECLARE_SERIAL`|是|是|[是]|  
  
#### <a name="to-use-basic-cobject-functionality"></a>若要使用基本 CObject 功能  
  
1.  用於衍生您的類別，從一般的 c + + 語法`CObject`(或從衍生自類別`CObject`)。  
  
     下列範例顯示簡單的情況下，從類別的衍生`CObject`:  
  
     [!code-cpp[NVC_MFCCObjectSample#1](../mfc/codesnippet/cpp/deriving-a-class-from-cobject_1.h)]  
  
 一般來說，不過，您可能想要覆寫的部分`CObject`的成員函式來處理您的新類別的特性。 例如，您通常可以覆寫`Dump`函式的`CObject`提供偵錯輸出的類別內容。 如需如何覆寫的詳細資訊`Dump`，請參閱文章[診斷： 傾印物件內容](http://msdn.microsoft.com/en-us/727855b1-5a83-44bd-9fe3-f1d535584b59)。 您也可以覆寫`AssertValid`函式的`CObject`提供自訂的測試，驗證資料成員的類別物件的一致性。 如需說明如何覆寫的`AssertValid`，請參閱[MFC ASSERT_VALID 和 CObject::AssertValid](http://msdn.microsoft.com/en-us/7654fb75-9e9a-499a-8165-0a96faf2d5e6)。  
  
 發行項[指定功能層級](../mfc/specifying-levels-of-functionality.md)描述如何指定其他層級的功能，包括執行階段類別資訊、 動態物件建立和序列化。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CObject](../mfc/using-cobject.md)

