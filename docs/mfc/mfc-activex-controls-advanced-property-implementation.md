---
title: MFC ActiveX 控制項： 進階屬性實作 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
ms.assetid: ec2e6759-5a8e-41d8-a275-99af8ff6f32e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4aa1116384ac9fd5212046f9a0b3354a3aa70d88
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416080"
---
# <a name="mfc-activex-controls-advanced-property-implementation"></a>MFC ActiveX 控制項：進階屬性實作

本文說明實作進階的 ActiveX 控制項中的屬性與相關的主題。

>[!IMPORTANT]
> ActiveX 是舊版的技術，不應用於新的開發。 如需有關取代 ActiveX 的現代技術的詳細資訊，請參閱[ActiveX 控制項](activex-controls.md)。

- [唯讀和唯寫屬性](#_core_read2donly_and_write2donly_properties)

- [從屬性中傳回的錯誤碼](#_core_returning_error_codes_from_a_property)

##  <a name="_core_read2donly_and_write2donly_properties"></a> 唯讀和唯寫屬性

加入屬性精靈 提供快速且輕鬆的方法，來實作控制項的唯讀或唯寫屬性。

#### <a name="to-implement-a-read-only-or-write-only-property"></a>若要實作唯讀或唯寫屬性

1. 載入控制項專案。

1. 在 [類別檢視] 中，展開控制項的程式庫節點。

1. 在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。

1. 從快顯功能表中，按一下**新增**，然後按一下**加入屬性**。

     這會開啟[加入屬性精靈](../ide/names-add-property-wizard.md)。

1. 在 **屬性名稱**方塊中，輸入您的屬性名稱。

1. 在 [實作類型] 中，按一下 [Get/Set 方法] 。

1. 在 **屬性的型別**方塊中，選取適當的型別屬性。

1. 如果您的唯讀屬性，請，清除 Set 函式名稱。 如果您的唯寫屬性，請，清除 Get 函式名稱。

9. 按一下 [ **完成**]。

當您這樣做時，加入屬性精靈插入函式`SetNotSupported`或`GetNotSupported`取代一般的分派對應項目中設定或取得函式。

如果您想要變更現有的屬性是唯讀或唯寫時，您可以手動編輯分派對應，並從控制項類別中移除不必要的 Set 或 Get 函式。

如果您想要有條件地唯讀或唯寫 （例如，只在您的控制項在特定模式下操作時，才） 的屬性，您可以提供 Set 或 Get 函式，為正常，並呼叫`SetNotSupported`或`GetNotSupported`函式在適當的地方。 例如: 

[!code-cpp[NVC_MFC_AxUI#29](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-property-implementation_1.cpp)]

此程式碼範例會呼叫`SetNotSupported`如果`m_bReadOnlyMode`資料成員 **，則為 TRUE**。 如果**FALSE**，則屬性會設定為新值。

##  <a name="_core_returning_error_codes_from_a_property"></a> 從屬性中傳回的錯誤碼

若要指出錯誤發生時嘗試取得或設定屬性，請使用`COleControl::ThrowError`函式，其採用 SCODE （狀態碼） 做為參數。 您可以使用預先定義的 SCODE 或定義您自己的其中一個。 如需預先定義的 SCODEs 及定義自訂 SCODEs 指示的清單，請參閱[處理您的 ActiveX 控制項中的錯誤](../mfc/mfc-activex-controls-advanced-topics.md)中發行項的 ActiveX 控制項： 進階主題。

Helper 函式存在的最常見預先定義的 SCODEs，例如[colecontrol:: Setnotsupported](../mfc/reference/colecontrol-class.md#setnotsupported)， [colecontrol:: Getnotsupported](../mfc/reference/colecontrol-class.md#getnotsupported)，和[colecontrol:: Setnotpermitted](../mfc/reference/colecontrol-class.md#setnotpermitted).

> [!NOTE]
>  `ThrowError` 適用於只做為傳回從錯誤中屬性的 Get 或 Set 函式或自動化方法。 這些只適用於適當的例外狀況處理常式會出現在堆疊上的時候。

如需有關報告的程式碼在其他區域中的例外狀況的詳細資訊，請參閱[colecontrol:: Fireerror](../mfc/reference/colecontrol-class.md#fireerror)和區段[處理您的 ActiveX 控制項中的錯誤](../mfc/mfc-activex-controls-advanced-topics.md)文中所 ActiveX 控制項： 進階主題。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX 控制項：屬性](../mfc/mfc-activex-controls-properties.md)<br/>
[MFC ActiveX 控制項：方法](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl 類別](../mfc/reference/colecontrol-class.md)
