---
title: "ATL 控制項精靈 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.codewiz.class.atl.control.overview
dev_langs: C++
helpviewer_keywords:
- ATL projects, adding controls
- controls [ATL], adding to projects
- ATL Control Wizard
ms.assetid: 991f8e72-ffbc-4382-a4ce-e255acfba5b6
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5a9167153c2b827e1bc2597e830e9b3c82ee31b7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="atl-control-wizard"></a>ATL 控制項精靈
ATL 專案 （或具有 ATL 支援的 MFC 專案） 插入 ATL 控制項。 您可以使用此精靈將控制項的三種：  
  
-   標準控制項  
  
-   複合控制項  
  
-   DHTML 控制項  
  
 此外，您可以指定最小的控制項，移除從介面[介面](../../atl/reference/interfaces-atl-control-wizard.md)清單中，提供做為預設值，以開啟 多數容器中的控制項。 您可以設定要支援中的控制項的介面**介面**精靈頁面。  
  
## <a name="remarks"></a>備註  
 此精靈所產生註冊指令碼會登錄其 COM 元件，而不是 HKEY_LOCAL_MACHINE hkey_current_user 之下。 若要修改這個行為，請設定**註冊元件的所有使用者**ATL 精靈的選項。  
  
## <a name="names"></a>名稱  
 指定之名稱的物件、 介面和類別新增至您的專案。 除了**簡短名稱**，所有其他方塊可以獨立變更。 如果您變更的文字**簡短名稱**，變更會反映在此頁面中的所有其他方塊的名稱。 如果您變更**Coclass**名稱在 COM 區段中，變更會反映在**類型** 方塊中，但**介面**名稱和**ProgID**嗎無法變更。 這項命名行為被為了讓您開發您的控制項時容易識別的所有名稱。  
  
> [!NOTE]
>  **Coclass**在未使用屬性的控制項上編輯。 如果您的專案屬性，則無法編輯**Coclass**。  
  
### <a name="c"></a>C++  
 提供 c + + 類別來實作物件建立的資訊。  
  
 **簡短名稱**  
 設定物件的縮寫的名稱。 您提供的名稱會決定類別和**Coclass**名稱、 檔案 (。CPP 和。H） 名稱的介面名稱，而**類型**名稱，除非您個別變更這些欄位。  
  
 **類別**  
 設定之類別的實作物件的名稱。 這個名稱根據您在中提供的名稱**簡短名稱**，前面會加 'C'、 類別名稱的一般前置詞上。  
  
 **.h 檔案**  
 設定新的物件類別的標頭檔的名稱。 根據預設，這個名稱根據您在中提供的名稱**簡短名稱**。 按一下省略符號按鈕，將檔案名稱儲存到您選擇的位置，或將類別宣告附加至現有的檔案。 如果您選取現有的檔案，精靈會無法將其儲存到選取的位置直到您按一下**完成**。  
  
 精靈不會覆寫檔案。 如果當您按一下 選取現有的檔案名稱**完成**，精靈會提示您是否要在類別宣告附加至檔案的內容。 按一下**是**附加檔案，按一下 **否**返回精靈並指定另一個檔案名稱。  
  
 **.cpp 檔案中**  
 設定新的物件類別的實作檔名稱。 根據預設，這個名稱根據您在中提供的名稱**簡短名稱**。 按一下省略符號按鈕，將檔案名稱儲存到您選擇的位置。 直到您按一下該檔案不儲存選取的位置**完成**精靈中。  
  
 精靈不會覆寫檔案。 如果當您按一下 選取現有的檔案名稱**完成**，精靈會提示您是否要在類別實作附加至檔案的內容。 按一下**是**附加檔案，按一下 **否**返回精靈並指定另一個檔案名稱。  
  
 **使用屬性**  
 指出物件是否使用屬性。 如果您要將物件加入 ATL 屬性化專案，這個選項是選取和無法變更。 亦即，您可以建立以屬性支援的專案加入屬性化的物件。  
  
 您可以加入屬性化的物件只會使用屬性的 ATL 專案。 如果您選取此選項並沒有支援的屬性之 ATL 專案時，精靈會提示您指定是否要將屬性支援加入至專案。  
  
 根據預設，加入您在設定此選項之後的任何物件會指定為屬性化 （核取方塊已選取）。 您可以清除此方塊可將不會使用屬性的物件。  
  
 請參閱[ATL 專案精靈、 應用程式設定](../../atl/reference/application-settings-atl-project-wizard.md)和[屬性的基本機制](../../windows/basic-mechanics-of-attributes.md)如需詳細資訊。  
  
### <a name="com"></a>COM  
 提供物件的 COM 功能的相關資訊。  
  
 **Coclass**  
 設定包含一份物件支援的介面的元件類別的名稱。  
  
> [!NOTE]
>  如果您使用建立的專案屬性，或如果您在此精靈頁面指示控制項使用屬性，您就無法變更此選項，因為 ATL 不包含**coclass**屬性。  
  
 **Interface**  
 設定物件的介面名稱。 根據預設介面名稱前面加上"I"。  
  
 **Type**  
 設定會在登錄中的物件描述  
  
 **ProgID**  
 設定容器可以使用而不是物件的 CLSID 的名稱。 不會自動填入此欄位。 如果您不會手動填入此欄位，控制項可能無法使用其他工具。 例如，ActiveX 控制項，而不會產生`ProgID`不適用於**插入 ActiveX 控制項** 對話方塊。 如需 對話方塊的詳細資訊，請參閱[插入 ActiveX 控制項對話方塊](../../windows/insert-activex-control-dialog-box.md)。  
  
## <a name="see-also"></a>請參閱  
 [ATL 控制項](../../atl/reference/adding-an-atl-control.md)   
 [將功能加入至複合控制項](../../atl/adding-functionality-to-the-composite-control.md)   
 [ATL COM 物件的基本概念](../../atl/fundamentals-of-atl-com-objects.md)

