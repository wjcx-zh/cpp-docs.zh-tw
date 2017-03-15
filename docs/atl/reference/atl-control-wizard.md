---
title: "ATL 控制項精靈 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.control.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding controls
- controls [ATL], adding to projects
- ATL Control Wizard
ms.assetid: 991f8e72-ffbc-4382-a4ce-e255acfba5b6
caps.latest.revision: 17
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
ms.sourcegitcommit: 4fafe461008e3545243d693e0d9e34acd57163e0
ms.openlocfilehash: 586ac14878ccd6908d025d706b72f3c9856d1b39
ms.lasthandoff: 02/24/2017

---
# <a name="atl-control-wizard"></a>ATL 控制項精靈
ATL 專案 （或具有 ATL 支援的 MFC 專案） 插入 ATL 控制項。 您可以使用此精靈將控制項的三種︰  
  
-   標準控制項  
  
-   複合控制項  
  
-   DHTML 控制項  
  
 此外，您可以指定最小的控制項，移除介面從[介面](../../atl/reference/interfaces-atl-control-wizard.md)清單中，提供做為預設值，以開啟 多數容器中的控制項。 您可以設定要在控制項支援的介面**介面**精靈頁面。  
  
## <a name="remarks"></a>備註  
 此精靈所產生的註冊指令碼會登錄其 COM 元件，而不是 HKEY_LOCAL_MACHINE hkey_current_user 之下。 若要修改此行為，請設定**註冊元件的所有使用者**ATL 精靈的選項。  
  
## <a name="names"></a>名稱  
 指定物件、 介面和類別新增至您的專案的名稱。 除了**簡短名稱**，其他方塊都可以獨立變更。 如果您變更的文字**簡短名稱**，變更會反映在此頁面中的所有其他方塊的名稱。 如果您變更**Coclass**名稱在 COM 區段中，變更會反映在**類型** 方塊中，但**介面**名稱和**ProgID**不會變更。 此命名的行為被設計來讓您在開發控制項時很容易辨識所有的名稱。  
  
> [!NOTE]
>  **Coclass**化的控制項上編輯。 如果您的專案屬性，則無法編輯**Coclass**。  
  
### <a name="c"></a>C++  
 提供建立來實作物件的 c + + 類別的資訊。  
  
 **簡短名稱**  
 設定物件的縮寫的名稱。 您提供的名稱將決定類別和**Coclass**名稱、 檔案 (。CPP 和。H） 名稱的介面名稱，而**類型**名稱，除非您個別變更這些欄位。  
  
 **類別**  
 設定實作物件的類別名稱。 這個名稱根據您在中提供的名稱**簡短名稱**、 前面 'C'、 類別名稱的一般前置詞加上。  
  
 **.h 檔案**  
 設定新的物件類別的標頭檔名稱。 根據預設，這個名稱根據您在中提供的名稱**簡短名稱**。 按一下省略符號按鈕，將檔案名稱儲存至您選擇的位置，或將類別宣告附加至現有的檔案。 如果您選取現有的檔案，精靈將不將它儲存到選取的位置直到您按一下**完成**。  
  
 精靈不會覆寫檔案。 如果當您按一下 選取現有的檔案名稱**完成**，精靈會提示您是否要在類別宣告附加至檔案的內容。 按一下 **是**附加檔案，按一下 **否**回到精靈，並指定另一個檔案名稱。  
  
 **.cpp 檔**  
 設定新的物件類別的實作檔名稱。 根據預設，這個名稱根據您在中提供的名稱**簡短名稱**。 按一下省略符號按鈕，將檔案名稱儲存至您選擇的位置。 直到您按一下該檔案不儲存選取的位置**完成**在精靈中。  
  
 精靈不會覆寫檔案。 如果當您按一下 選取現有的檔案名稱**完成**，精靈會提示您是否要在類別實作附加至檔案的內容。 按一下 **是**附加檔案，按一下 **否**回到精靈，並指定另一個檔案名稱。  
  
 **使用屬性**  
 指出物件是否使用屬性。 如果您要將物件加入屬性化 ATL 專案，這個選項是選取和無法變更。 也就是說，您可以將屬性化的物件加入屬性支援建立的專案。  
  
 您可以加入屬性化的物件只使用屬性的 ATL 專案。 如果您選取此選項也沒有支援的屬性為 ATL 專案時，精靈會提示您指定是否要將屬性支援加入至專案。  
  
 根據預設，設定這個選項之後新增任何物件會指定為屬性化 （選取核取方塊）。 您可以清除此方塊可將不會使用屬性的物件。  
  
 請參閱[ATL 專案精靈、 應用程式設定](../../atl/reference/application-settings-atl-project-wizard.md)和[屬性的基本機制](../../windows/basic-mechanics-of-attributes.md)如需詳細資訊。  
  
### <a name="com"></a>COM  
 提供物件的 COM 功能的相關資訊。  
  
 **Coclass**  
 設定元件類別，其中包含的物件支援的介面清單的名稱。  
  
> [!NOTE]
>  如果您使用建立的專案屬性，或如果您在此精靈頁面指示控制項使用屬性，您就無法變更此選項，因為 ATL 不包含**coclass**屬性。  
  
 **介面**  
 設定物件的介面名稱。 根據預設介面名稱前面會加上"I"。  
  
 **Type**  
 設定會出現在登錄中的物件描述  
  
 **ProgID**  
 設定名稱，而不是物件的 CLSID 可用容器。 不會自動填入這個欄位。 如果您不會手動填入此欄位，控制項可能無法使用其他工具。 例如，ActiveX 控制項，而不會產生`ProgID`不適用於**插入 ActiveX 控制項**對話方塊。 如需有關此對話方塊，請參閱[插入 ActiveX 控制項對話方塊](../../windows/insert-activex-control-dialog-box.md)。  
  
## <a name="see-also"></a>另請參閱  
 [ATL 控制項](../../atl/reference/adding-an-atl-control.md)   
 [將功能加入至複合控制項](../../atl/adding-functionality-to-the-composite-control.md)   
 [ATL COM 物件的基本概念](../../atl/fundamentals-of-atl-com-objects.md)


