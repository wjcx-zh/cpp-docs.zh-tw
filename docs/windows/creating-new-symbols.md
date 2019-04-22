---
title: HOW TO：建立符號 (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.symbol.creating
- vc.editors.symbol.managing
- vc.editors.resourcesymbols
- vc.editors.symbol.resource
helpviewer_keywords:
- New Symbol dialog box [C++]
- symbols [C++], creating
- resources [C++], viewing
- resource symbols
- symbols [C++], viewing
- New Symbol dialog box [C++]
- Resource Symbols dialog box [C++]
- Change Symbol dialog box [C++]
- resource symbols
- View Use button
- resource editors [C++], resource symbols
ms.assetid: 35168d31-3af6-4ecd-9362-3707d47b53f3
ms.openlocfilehash: 8bb73c1a9e8d253492a7068c444dd7ddea8417da
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59026353"
---
# <a name="how-to-create-symbols-c"></a>HOW TO：建立符號 (C++)

當您開始新的專案時，您可能會發現它方便您需要在之前建立的資源，它們會被指派的符號名稱對應。

> [!NOTE]
> 如果您的專案尚未包含.rc 檔，請參閱[How to:建立資源](../windows/how-to-create-a-resource-script-file.md)。

**資源符號**對話方塊可讓您加入新的資源符號、 變更顯示，或請跳至原始程式碼中正在使用中位置的符號。

對話方塊包含下列屬性：

|屬性|描述|
|--------------------------|------------------------------------------|
|**名稱**|顯示的符號名稱。<br/><br/>如需詳細資訊，請參閱 <<c0> [ 符號名稱限制](../windows/symbol-name-restrictions.md)。|
|**值**|顯示符號的數值。<br/><br/>如需詳細資訊，請參閱 <<c0> [ 符號值限制](../windows/symbol-value-restrictions.md)。|
|**使用中**|選取時，指定符號正由一或多個資源使用。<br/><br/>資源所述**供** 方塊中。|
|**顯示唯讀符號**|選取時，顯示唯讀資源。<br/><br/>根據預設，**資源符號**對話方塊會顯示可修改的資源在資源指令碼檔案中，但選取這個選項，可修改的資源會以粗體文字以及唯讀資源會以純文字。|
|**使用**|使用在符號清單中選取的符號來顯示一或多個資源。<br/><br/>若要移到編輯器中指定的資源，請選取中的資源**供**方塊，然後選擇**檢視使用**。|
|**新增**|開啟**新符號**，可讓您定義名稱 對話方塊中，如有必要，新的符號資源識別項的值。|
|**變更**|會開啟**變更符號**對話方塊中，可讓您變更名稱或符號的值。<br/><br/>如果符號用於使用中的控制項或資源，只可以從對應的資源編輯器變更符號。 如需詳細資訊，請參閱 <<c0> [ 管理符號](../windows/changing-unassigned-symbols.md)。|
|**檢視使用**|開啟在對應資源編輯器中含有符號的資源。|

## <a name="create-symbols"></a>建立符號

### <a name="to-create-a-new-symbol"></a>若要建立新的符號

1. 在 **資源符號**對話方塊方塊中，選擇**新增**。

1. 在 **名稱**方塊中，輸入符號名稱。

1. 接受指定的符號值，或輸入新的值，在**值** 方塊中。

1. 選取 **確定**新符號加入符號清單。

> [!NOTE]
> 如果您輸入的符號名稱已經存在，此時會出現訊息方塊，說明已定義使用該名稱的符號。 您不能定義兩個或多個具有相同的名稱，符號，但您可以定義具有相同數值的不同符號。

## <a name="to-view-resource-symbols"></a>檢視資源符號

在 [[資源檢視](how-to-create-a-resource-script-file.md#create-resources)，以滑鼠右鍵按一下您 *.rc*檔案，然後選取**資源符號**若要檢視資源符號表中的**資源符號**] 對話方塊。

> [!NOTE]
> 若要查看預先定義的符號，請檢查**顯示唯讀符號**核取方塊。

### <a name="to-open-the-resource-editor-for-a-given-symbol"></a>若要開啟指定符號的資源編輯器

當您瀏覽中的符號**資源符號**，您可能想要特定符號的使用方式的詳細資訊。 **檢視使用**按鈕提供快速的方式，來取得此資訊。

1. 在 [**資源符號**] 對話方塊中的**名稱**方塊中，選取一個符號。

1. 在 **被使用**方塊中，選取您感興趣的資源類型。

1. 選取 [**檢視使用**] 按鈕。

   資源會出現在適當的編輯器視窗中。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資源識別項 (符號)](../windows/symbols-resource-identifiers.md)<br/>
[如何：管理符號](../windows/changing-a-symbol-or-symbol-name-id.md)<br/>
[預先定義的符號識別碼](../windows/predefined-symbol-ids.md)<br/>