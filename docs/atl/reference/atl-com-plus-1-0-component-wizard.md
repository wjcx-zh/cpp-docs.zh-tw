---
title: "ATL COM + 1.0 元件精靈 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.mts.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding components
- ATL COM+ 1.0 Component Wizard
ms.assetid: 11670681-8671-4122-96a4-2e52f8dadce0
caps.latest.revision: 13
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 2729975c5e823965f4f5c16d5bfe317ce10a3670
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="atl-com-10-component-wizard"></a>ATL COM+ 1.0 元件精靈
使用此精靈將物件新增至您的專案，以支援 COM + 1.0 服務，包括交易。  
  
 您可以指定物件是否支援雙重介面和自動化。 您也可以指示錯誤資訊介面、 增強的物件控制項、 交易和非同步訊息佇列的支援。  
  
## <a name="remarks"></a>備註  
 開頭為[!INCLUDE[vs_orcas_long](../../atl/reference/includes/vs_orcas_long_md.md)]，此精靈所產生的註冊指令碼將會註冊 COM 元件在**HKEY_CURRENT_USER**而不是**HKEY_LOCAL_MACHINE**。 若要修改此行為，請設定**註冊元件的所有使用者**ATL 精靈的選項。  
  
## <a name="names"></a>名稱  
 指定物件、 介面和類別新增至您的專案的名稱。 除了**簡短名稱**，其他方塊都可以獨立編輯。 如果您變更的文字**簡短名稱**，變更會反映在此頁面中的所有其他方塊的名稱。 如果您變更**Coclass**名稱在 COM 區段中，變更會反映在**類型**和**ProgID**  方塊中，但**介面**名稱不會變更。 此命名的行為被設計來讓您在開發控制項時很容易辨識所有的名稱。  
  
 **簡短名稱**  
 設定物件的縮寫的名稱。 您提供決定名稱`Class`和`Coclass`名稱， **.cpp 檔案中**和**.h 檔案**名稱，**介面**名稱，**類型**名稱，而**ProgID**，除非您個別變更這些欄位。  
  
 **.h 檔案**  
 設定新的物件類別的標頭檔名稱。 根據預設，這個名稱根據您在中提供的名稱**簡短名稱**。 按一下省略符號按鈕，將檔案名稱儲存至您選擇的位置，或將類別宣告附加至現有的檔案。 如果您選擇現有的檔案，精靈將不將它儲存到選取的位置直到您按一下**完成**在精靈中。  
  
 精靈不會覆寫檔案。 如果當您按一下 選取現有的檔案名稱**完成**，精靈會提示您是否要在類別宣告附加至檔案的內容。 按一下 **是**附加檔案，按一下  **No**回到精靈，並指定另一個檔案名稱。  
  
 **類別**  
 設定要建立之類別的名稱。 這個名稱根據您在提供的名稱**簡短名稱**、 前面 'C'、 類別名稱的一般前置詞加上。  
  
 **.cpp 檔**  
 設定新的物件類別的實作檔名稱。 根據預設，這個名稱會根據您在提供的名稱上**簡短名稱**。 按一下省略符號按鈕，將檔案名稱儲存至您選擇的位置。 直到您按一下該檔案不儲存選取的位置**完成**在精靈中。  
  
 精靈不會覆寫檔案。 如果當您按一下 選取現有的檔案名稱**完成**，精靈會提示您是否要在類別實作附加至檔案的內容。 按一下 **是**附加檔案，按一下  **No**回到精靈，並指定另一個檔案名稱。  
  
 **使用屬性**  
 指出物件是否使用屬性。 如果您要將物件加入屬性化 ATL 專案，這個選項是選取和無法變更。 也就是說，您可以將屬性化的物件加入屬性支援建立的專案。  
  
 如果您選取此選項也沒有支援的屬性為 ATL 專案時，精靈會提示您指定是否要將屬性支援加入至專案。  
  
 設定這個選項之後新增的所有物件都會都指定為屬性的預設 （選取核取方塊）。 您可以清除此方塊可將不會使用屬性的物件。  
  
 請參閱[ATL 專案精靈、 應用程式設定](../../atl/reference/application-settings-atl-project-wizard.md)和[屬性的基本機制](../../windows/basic-mechanics-of-attributes.md)如需詳細資訊。  
  
### <a name="com"></a>COM  
 提供物件的 COM 功能的相關資訊。  
  
 **Coclass**  
 設定元件類別，其中包含的物件支援的介面清單的名稱。  
  
> [!NOTE]
>  如果您使用建立的專案屬性，或如果您在此精靈頁面上指示 COM + 1.0 元件會使用屬性，您就無法變更此選項，因為 ATL 不包含`coclass`屬性。  
  
 **Type**  
 設定會出現在登錄中的物件描述  
  
 **介面**  
 設定您建立物件的介面。 這個介面包含自訂的方法。  
  
 **ProgID**  
 設定名稱，而不是物件的 CLSID 可用容器。  
  
## <a name="see-also"></a>另請參閱  
 [ATL COM + 1.0 元件](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)


