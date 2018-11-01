---
title: ATL 控制項精靈
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.control.overview
helpviewer_keywords:
- ATL projects, adding controls
- controls [ATL], adding to projects
- ATL Control Wizard
ms.assetid: 991f8e72-ffbc-4382-a4ce-e255acfba5b6
ms.openlocfilehash: a7fd85263531968aeb4dd86534b4e67ddc553629
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598818"
---
# <a name="atl-control-wizard"></a>ATL 控制項精靈

插入至 ATL 專案 （或 MFC 與 ATL 支援加入專案） ATL 控制項。 您可以使用此精靈將其中一個控制項的三種：

- 標準控制項

- 複合控制項

- DHTML 控制項

此外，您可以指定最小的控制項，移除從介面[介面](../../atl/reference/interfaces-atl-control-wizard.md)清單中，提供做為預設值，在大部分的容器中開啟的控制項。 您可以設定您想要支援中的控制項的介面**介面**精靈頁面。

## <a name="remarks"></a>備註

此精靈所產生的註冊指令碼會登錄其 COM 元件，而不是 HKEY_LOCAL_MACHINE hkey_current_user。 若要修改此行為，請設定**為所有使用者的註冊元件**ATL 精靈的選項。

## <a name="names"></a>名稱

指定物件、 介面和類別新增至您的專案的名稱。 除了**簡短名稱**，其他所有方塊可以獨立都變更。 如果您變更的文字**簡短名稱**，變更會反映在這個頁面中的所有其他方塊的名稱。 如果您變更**Coclass**名稱在 COM 區段中，變更會反映在**型別** 方塊中，但**介面**名稱並**ProgID**嗎無法變更。 此命名的行為可讓您開發您的控制項時輕鬆地識別所有的名稱。

> [!NOTE]
>  **Coclass**編輯上未使用屬性的控制項。 如果您的專案屬性，您無法編輯**Coclass**。

### <a name="c"></a>C++

提供建立來實作物件的 c + + 類別的資訊。

- **簡短名稱**

   設定物件的縮寫的名稱。 您所提供的名稱會決定類別及**Coclass**名稱、 檔案 (。CPP 和。H） 名稱，介面名稱，而**型別**名稱，除非您個別變更這些欄位。

- **類別**

   設定之類別的實作物件的名稱。 這個名稱根據您在中提供的名稱**簡短名稱**前面 'C'，類別名稱的一般前置詞加上。

- **.h 檔案**

   設定新物件類別的標頭檔名稱。 根據預設，這個名稱根據您在中提供的名稱**簡短名稱**。 按一下省略符號按鈕，將檔案名稱儲存至您選擇的位置，或將類別宣告附加至現有的檔案。 如果您選取現有的檔案時，精靈會不將其儲存至選取的位置直到您按一下**完成**。

   精靈不會覆寫檔案。 如果您選取現有檔案的名稱，當您按一下 [完成] 時，精靈會提示您指出是否應該將類別宣告附加至檔案的內容。 按一下 [是] 可附加檔案，按一下 [否] 可返回精靈並指定另一個檔案名稱。

- **.cpp 檔案**

   設定新物件類別的實作檔名稱。 根據預設，這個名稱根據您在中提供的名稱**簡短名稱**。 按一下省略符號按鈕，將檔案名稱儲存至您選擇的位置。 在您按一下精靈中的 [完成] 之前，檔案不會儲存至選取的位置。

   精靈不會覆寫檔案。 如果您選取現有檔案的名稱，當您按一下 [完成] 時，精靈會提示您指出是否應該將類別實作附加至檔案的內容。 按一下 [是] 可附加檔案，按一下 [否] 可返回精靈並指定另一個檔案名稱。

- **使用屬性**

   指出物件是否使用屬性。 如果您要為屬性化 ATL 專案中新增物件，此選項已選取不可以變更。 也就是說，您可以將屬性化的物件加入建立以屬性支援的專案。

   您可以加入屬性化的物件只會使用屬性的 ATL 專案。 如果您選取此選項，ATL 專案，並沒有支援的屬性，精靈會提示您指定是否要將屬性支援加入至專案。

   根據預設，加入您在設定此選項之後的任何物件會指定為屬性化 （核取方塊已選取）。 您可以清除此方塊，將不會使用屬性的物件。

   請參閱[ATL 專案精靈、 應用程式設定](../../atl/reference/application-settings-atl-project-wizard.md)並[屬性的基本機制](../../windows/basic-mechanics-of-attributes.md)如需詳細資訊。

### <a name="com"></a>COM

提供物件的 COM 功能的相關資訊。

- **Coclass**

   設定元件類別，其中包含的物件所支援的介面清單的名稱。

   > [!NOTE]
   > 如果您建立您的專案使用的屬性，或如果您在此精靈頁面指示控制項使用的屬性，您就無法變更此選項，因為不包含 ATL **coclass**屬性。

- **Interface**

   設定物件之介面的名稱。 預設的介面名稱前面會加上"I"。

- **Type**

   設定會在登錄中的物件描述

- **ProgID**

   設定而不是物件的 CLSID 可用容器的名稱。 不會自動填入此欄位。 如果您不會手動填入這個欄位，控制項可能無法與其他工具。 例如，ActiveX 控制項，而不會產生`ProgID`不適用於**插入 ActiveX 控制項** 對話方塊。 如需對話方塊的詳細資訊，請參閱[插入 ActiveX 控制項對話方塊](../../windows/insert-activex-control-dialog-box.md)。

## <a name="see-also"></a>另請參閱

[ATL 控制項](../../atl/reference/adding-an-atl-control.md)<br/>
[將功能新增至複合控制項](../../atl/adding-functionality-to-the-composite-control.md)<br/>
[ATL COM 物件的基本概念](../../atl/fundamentals-of-atl-com-objects.md)

