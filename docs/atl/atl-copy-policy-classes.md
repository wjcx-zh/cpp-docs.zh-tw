---
title: ATL 複製原則類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- data [C++], ATL
- classes [C++], copy policy
- copy policy classes [C++]
- _Copy class
- _CopyInterface class
ms.assetid: 06704b68-d318-4c5d-a65b-71457fe9d00d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 34b9ed5dca45633a5ab980d38b8a7cda151f5dc7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358523"
---
# <a name="atl-copy-policy-classes"></a>ATL 複製原則類別
複製原則類別是[公用程式類別](../atl/utility-classes.md)用來初始化、 複製和刪除資料。 複製原則類別可讓您定義的資料，任何類型的複製語意，並定義不同的資料類型之間的轉換。  
  
 ATL 使用複製原則類別中實作的下列範本：  
  
-   [CComEnumImpl](../atl/reference/ccomenumimpl-class.md)  
  
-   [IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)  
  
-   [ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)  
  
 藉由封裝複製或轉換中複製的原則類別，可作為範本引數傳遞的資料所需的資訊，ATL 開發人員已提供的這些類別極端重複使用性。 例如，如果您需要實作使用任何任意的資料類型的集合，您只需要提供是適當的複製原則;您完全不需要實作集合的程式碼。  
  
## <a name="definition"></a>定義  
 根據定義，這個類別提供下列靜態函式是複製原則類別：  
  
 `static void init(` `DestinationType` `* p);`  
  
 `static HRESULT copy(` `DestinationType` `* pTo, const`  `SourceType` `* pFrom);`  
  
 `static void destroy(` `DestinationType` `* p);`  
  
 您可以取代類型`DestinationType`和*SourceType*複本的每個原則的任意資料類型。  
  
> [!NOTE]
>  雖然您可以定義複製任何任意的資料類型的原則類別，使用 ATL 程式碼中的類別應該限制為有意義的類型。 例如，當使用複製原則類別與 ATL 的集合或列舉值實作`DestinationType`必須可以當做 COM 介面方法中的參數類型。  
  
 使用**init**初始化資料，**複製**複製資料，以及**終結**釋放資料。 初始化的確切意義、 複製和解構複製 policy 類別的網域，而且會根據相關的資料類型而有所不同。  
  
 有兩項需求的使用和複製原則類別的實作：  
  
-   第一個參數**複製**必須只接收先前初始化使用的資料指標**init**。  
  
-   **終結**必須永遠只會接收您先前初始化使用的資料指標**init**或透過複製**複製**。  
  
## <a name="standard-implementations"></a>標準的實作  
 ATL 提供兩個複本原則類別的形式 **_Copy**和 **_CopyInterface**樣板類別：  
  
-   **_Copy**類別可讓同質只複製 （不轉換資料類型之間） 因為它只提供單一的樣板參數同時指定`DestinationType`和*SourceType*。 此範本的一般實作包含未初始化或解構的程式碼，並使用`memcpy`複製資料。 ATL 也提供特製化的 **_Copy**如**VARIANT**， `LPOLESTR`， **OLEVERB**，和**CONNECTDATA**資料型別。  
  
-   **_CopyInterface**類別提供複製下列標準的 COM 規則的介面指標的實作。 再次這個類別允許只複製，因此它會使用簡單的設定，以及呼叫`AddRef`執行複製。  
  
## <a name="custom-implementations"></a>自訂實作  
 一般而言，您必須定義您自己的複製原則類別異質複製 （也就是資料類型之間的轉換）。 如需自訂複製原則類別的一些範例，查看 VCUE_Copy.h 和 VCUE_CopyString.h 中的檔案[ATLCollections](../visual-cpp-samples.md)範例。 這些檔案包含兩個範本複製原則類別，`GenericCopy`和`MapCopy`，加上數字的特製化的`GenericCopy`不同資料類型。  
  
### <a name="genericcopy"></a>GenericCopy  
 `GenericCopy` 可讓您指定*SourceType*和`DestinationType`當做範本引數。 以下是最常見的形式`GenericCopy`VCUE_Copy.h 類別：  
  
 [!code-cpp[NVC_ATL_COM#30](../atl/codesnippet/cpp/atl-copy-policy-classes_1.h)]  
  
 VCUE_Copy.h 也包含下列的特製化此類別： `GenericCopy<BSTR>`， `GenericCopy<VARIANT, BSTR>`， `GenericCopy<BSTR, VARIANT>`。 VCUE_CopyString.h 包含從複製的特製化**std:: string**s: `GenericCopy<std::string>`， `GenericCopy<VARIANT, std::string>`，和`GenericCopy<BSTR, std::string>`。 您可以加強`GenericCopy`進一步提供您自己的特製化。  
  
### <a name="mapcopy"></a>MapCopy  
 `MapCopy` 假設正在複製的資料會儲存成 c + + 標準程式庫樣式地圖中，因此它可讓您指定的 map 中的資料儲存和的目的地類型的類型。 類別的實作只會使用所提供的 typedef*此行*類別來判斷來源資料類型，並呼叫適當`GenericCopy`類別。 這個類別的任何特製化所不需。  
  
 [!code-cpp[NVC_ATL_COM#31](../atl/codesnippet/cpp/atl-copy-policy-classes_2.h)]  
  
## <a name="see-also"></a>另請參閱  
 [實作與 c + + 標準程式庫為基礎的集合](../atl/implementing-an-stl-based-collection.md)   
 [ATLCollections 範例](../visual-cpp-samples.md)

