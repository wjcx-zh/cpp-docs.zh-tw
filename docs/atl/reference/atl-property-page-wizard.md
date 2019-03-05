---
title: ATL 屬性頁精靈
ms.date: 10/03/2018
f1_keywords:
- vc.codewiz.class.atl.ppg.overview
helpviewer_keywords:
- ATL projects, adding property pages
- ATL Property Page Wizard
ms.assetid: 6113e325-facd-4f68-b491-144d75209922
ms.openlocfilehash: 791901ab3181ad2c8ac862a970980250693d20f7
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57258277"
---
# <a name="atl-property-page-wizard"></a>ATL 屬性頁精靈

此精靈[新增至 ATL 專案的屬性頁](../../atl/reference/adding-an-atl-property-page.md)或 MFC 與 ATL 支援加入專案。 ATL 屬性頁來設定屬性提供使用者介面 （或呼叫的方法） 的一或多個 COM 物件。

> [!WARNING]
> 在 Visual Studio 2017 15.9 版中，此程式碼精靈已淘汰，並且將從 Visual Studio 的未來版本中移除。 使用者很少用到這個精靈。 移除此精靈不會影響 ATL 和 MFC 的一般支援。 如果您想要分享關於此項淘汰的意見反應，請填寫[此問卷](https://www.surveymonkey.com/r/QDWKKCN)。 我們非常重視您的意見反應。

## <a name="remarks"></a>備註

從 Visual Studio 2008 開始，此精靈所產生的註冊指令碼會註冊其下的 COM 元件**HKEY_CURRENT_USER**而不是**HKEY_LOCAL_MACHINE**。 若要修改此行為，請設定**為所有使用者的註冊元件**ATL 精靈的選項。

## <a name="names"></a>名稱

指定物件、 介面和類別新增至您的專案的名稱。 除了**簡短名稱**，可獨立編輯所有其他的方塊。 如果您變更的文字**簡短名稱**，變更會反映在這個頁面中的所有其他方塊的名稱。 如果您變更**Coclass**名稱在 [COM] 區段中，變更會反映在**型別**並**ProgID**方塊。 此命名的行為可讓您開發您的屬性頁時輕鬆地識別所有名稱。

> [!NOTE]
>  **Coclass**是只有非屬性化專案上編輯。 如果您的專案屬性，您無法編輯**Coclass**。

### <a name="c"></a>C++

提供建立來實作物件的 c + + 類別的資訊。

|||
|-|-|
|詞彙|定義|
|**簡短名稱**|設定物件的縮寫的名稱。 您所提供的名稱會決定類別和**Coclass**名稱、 檔案 (**.cpp**並 **.h**) 名稱，**類型**名稱，以及**ProgID**，除非您個別變更這些欄位。|
|**.h 檔案**|設定新物件類別的標頭檔名稱。 根據預設，這個名稱根據您在中提供的名稱**簡短名稱**。 按一下省略符號按鈕，將檔案名稱儲存至您選擇的位置，或將類別宣告附加至現有的檔案。 如果您選取現有的檔案時，精靈會不將其儲存至選取的位置直到您按一下**完成**精靈中。<br /><br /> 精靈不會覆寫檔案。 如果您選取現有檔案的名稱，當您按一下 [完成] 時，精靈會提示您指出是否應該將類別宣告附加至檔案的內容。 按一下 [是] 可附加檔案，按一下 [否] 可返回精靈並指定另一個檔案名稱。|
|**類別**|設定之類別的實作物件的名稱。 這個名稱根據您在中提供的名稱**簡短名稱**前面 'C'，類別名稱的一般前置詞加上。|
|**.cpp 檔**|設定新物件類別的實作檔名稱。 根據預設，這個名稱根據您在中提供的名稱**簡短名稱**。 按一下省略符號按鈕，將檔案名稱儲存至您選擇的位置。 在您按一下精靈中的 [完成] 之前，檔案不會儲存至選取的位置。<br /><br /> 精靈不會覆寫檔案。 如果您選取現有檔案的名稱，當您按一下 [完成] 時，精靈會提示您指出是否應該將類別實作附加至檔案的內容。 按一下 [是] 可附加檔案，按一下 [否] 可返回精靈並指定另一個檔案名稱。|
|**使用屬性**|指出物件是否使用屬性。 如果您要將物件加入屬性化 ATL 專案，選取此選項，而且變成無法使用，也就是您可以新增屬性化物件加入至專案，建立以屬性支援。<br /><br /> 您可以加入屬性化的物件只會使用屬性的 ATL 專案。 如果您選取此選項，ATL 專案，並沒有支援的屬性，精靈會提示您指定是否要將屬性支援加入至專案。<br /><br /> 根據預設，加入您在設定此選項之後的任何物件會指定為屬性化 （核取方塊已選取）。 您可以清除此方塊，將不會使用屬性的物件。<br /><br /> 請參閱[ATL 專案精靈、 應用程式設定](../../atl/reference/application-settings-atl-project-wizard.md)並[屬性的基本機制](../../windows/basic-mechanics-of-attributes.md)如需詳細資訊。|

### <a name="com"></a>COM

提供物件的 COM 功能的相關資訊。

- **Coclass**

   設定元件類別，其中包含的物件所支援的介面清單的名稱。

   > [!NOTE]
   > 如果您建立您的專案使用的屬性，或如果您在此精靈頁面指示的屬性頁會使用屬性，您就無法變更此選項，因為不包含 ATL`coclass`屬性。

- **Type**

   設定會在登錄中的物件描述

- **ProgID**

   設定而不是物件的 CLSID 可用容器的名稱。

## <a name="see-also"></a>另請參閱

[選項，ATL 屬性頁精靈](../../atl/reference/options-atl-property-page-wizard.md)<br/>
[字串，ATL 屬性頁精靈](../../atl/reference/strings-atl-property-page-wizard.md)<br/>
[例如：實作屬性頁](../../atl/example-implementing-a-property-page.md)
