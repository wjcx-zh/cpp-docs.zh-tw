---
title: "ATL 簡單物件精靈 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.codewiz.class.atl.simple.overview
dev_langs: C++
helpviewer_keywords:
- ATL projects, adding objects
- ATL Simple Object Wizard
ms.assetid: f7f85741-9aad-4543-a917-a29b996364da
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bfbb97f66065efd0a9ef06de0ff427e893610955
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="atl-simple-object-wizard"></a>ATL 簡單物件精靈
此精靈可將基本的 COM 物件插入至專案。 使用精靈的這個頁面來指定識別的 c + + 類別和物件和它的 COM 功能檔案的名稱。  
  
 使用[選項](../../atl/reference/options-atl-simple-object-wizard.md)頁面來指定物件的執行緒模型，它的彙總此精靈支援，以及是否支援雙重介面和自動化。 您也可以指示支援錯誤資訊介面、 連接點、 Internet Explorer 支援和無限制執行緒封送處理。  
  
## <a name="remarks"></a>備註  
 從 Visual Studio 2008 開始，此精靈所產生註冊指令碼會登錄其下的 COM 元件**HKEY_CURRENT_USER**而不是**HKEY_LOCAL_MACHINE**。 若要修改這個行為，請設定**註冊元件的所有使用者**ATL 精靈的選項。  
  
## <a name="names"></a>名稱  
 指定之名稱的物件、 介面和類別新增至您的專案。 除了**簡短名稱**，其他方塊都可以各自編輯。 如果您變更的文字**簡短名稱**，變更會反映在此頁面中的所有其他方塊的名稱。 如果您變更**Coclass**名稱在 COM 區段中，變更會反映在**類型**和**ProgID**  方塊中，但**介面**名稱不會變更。 這項命名行為被為了讓您開發您的控制項時容易識別的所有名稱。  
  
> [!NOTE]
>  **Coclass**未使用屬性的專案上編輯。 如果您的專案屬性，則無法編輯**Coclass**。  
  
## <a name="c"></a>C++  
 提供 c + + 類別建立物件的資訊。  
  
 **簡短名稱**  
 設定物件的縮寫的名稱。 您所提供名稱判斷`Class`和**Coclass**名稱**.cpp 檔**和**.h 檔案**名稱，**介面**名稱**類型**名稱，而**ProgID**，除非您個別變更這些欄位。  
  
 **.h 檔案**  
 設定新的物件類別的標頭檔的名稱。 根據預設，這個名稱根據您在中提供的名稱**簡短名稱**。 按一下省略符號按鈕，將檔案名稱儲存到您選擇的位置，或將類別宣告附加至現有的檔案。 如果您選取現有的檔案，精靈會無法將其儲存到選取的位置直到您按一下**完成**精靈中。  
  
 精靈不會覆寫檔案。 如果當您按一下 選取現有的檔案名稱**完成**，精靈會提示您是否要在類別宣告附加至檔案的內容。 按一下**是**附加檔案，按一下 **否**返回精靈並指定另一個檔案名稱。  
  
 **類別**  
 設定要建立之類別的名稱。 這個名稱根據您在中提供的名稱**簡短名稱**，前面會加 'C'、 類別名稱的一般前置詞上。  
  
 **.cpp 檔案中**  
 設定新的物件類別的實作檔名稱。 根據預設，這個名稱根據您在中提供的名稱**簡短名稱**。 按一下省略符號按鈕，將檔案名稱儲存到您選擇的位置。 直到您按一下該檔案不儲存選取的位置**完成**精靈中。  
  
 精靈不會覆寫檔案。 如果當您按一下 選取現有的檔案名稱**完成**，精靈會提示您是否要在類別實作附加至檔案的內容。 按一下**是**附加檔案，按一下 **否**返回精靈並指定另一個檔案名稱。  
  
 **使用屬性**  
 指出物件是否使用屬性。 如果您要將物件加入 ATL 屬性化專案，這個選項是選取和無法變更。 亦即，您可以建立以屬性支援的專案加入屬性化的物件。  
  
 您可以加入屬性化的物件只會使用屬性的 ATL 專案。 如果您選取此選項並沒有支援的屬性之 ATL 專案時，精靈會提示您指定是否要將屬性支援加入至專案。  
  
 根據預設，加入您在設定此選項之後的任何物件會指定為屬性化 （核取方塊已選取）。 您可以清除此方塊可將不會使用屬性的物件。  
  
 請參閱[ATL 專案精靈、 應用程式設定](../../atl/reference/application-settings-atl-project-wizard.md)和[屬性的基本機制](../../windows/basic-mechanics-of-attributes.md)如需詳細資訊。  
  
## <a name="com"></a>COM  
 提供物件的 COM 功能的相關資訊。  
  
 **Coclass**  
 設定包含一份物件支援的介面的元件類別的名稱。  
  
> [!NOTE]
>  如果您使用建立的專案屬性，或如果您在此精靈頁面指示物件使用屬性，您就無法變更此選項，因為 ATL 不包含`coclass`屬性。  
  
 **Type**  
 設定會在登錄中的物件描述  
  
 **Interface**  
 設定您建立物件的介面。 這個介面包含自訂的方法。  
  
 **ProgID**  
 設定容器可以使用而不是物件的 CLSID 的名稱。  
  
## <a name="see-also"></a>另請參閱  
 [ATL 簡單物件](../../atl/reference/adding-an-atl-simple-object.md)

