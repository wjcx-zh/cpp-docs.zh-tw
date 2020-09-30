---
title: 如何： (c + +) 建立符號
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
ms.openlocfilehash: 008d2ab420034e628251c08222bf2e9f723deab1
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504512"
---
# <a name="how-to-create-symbols-c"></a>如何： (c + +) 建立符號

當您開始新的專案時，您可能會發現在建立要指派給他們的資源之前，對應您需要的符號名稱是很方便的。

> [!NOTE]
> 如果您的專案尚未包含 .rc 檔，請參閱 [如何：建立資源](../windows/how-to-create-a-resource-script-file.md)。

[ **資源符號** ] 對話方塊可讓您加入新的資源符號、變更顯示的符號，或跳到原始程式碼中使用符號的位置。

此對話方塊包含下列屬性：

|屬性|描述|
|--------------------------|------------------------------------------|
|**名稱**|顯示的符號名稱。<br/><br/>如需詳細資訊，請參閱 [符號名稱限制](./changing-a-symbol-or-symbol-name-id.md)。|
|**值**|顯示符號的數值。<br/><br/>如需詳細資訊，請參閱 [符號值限制](./changing-a-symbol-or-symbol-name-id.md)。|
|**使用中**|選取時，指定符號正由一或多個資源使用。<br/><br/>資源或資源會列在 [ **消費者** ] 方塊中。|
|**顯示唯讀符號**|選取時，顯示唯讀資源。<br/><br/>依預設，[ **資源符號** ] 對話方塊只會在您的資源腳本檔案中顯示可修改的資源，但在選取此選項之後，可修改的資源會以粗體文字顯示，且唯讀資源會以純文字顯示。|
|**使用對象**|使用在符號清單中選取的符號來顯示一或多個資源。<br/><br/>若要移至指定資源的編輯器，請選取 [ **消費者** ] 方塊中的資源，然後選擇 [ **視圖使用**]。|
|**新增**|開啟 [ **新增符號** ] 對話方塊，可讓您定義名稱，並視需要定義新符號資源識別碼的值。|
|**變更**|開啟 [ **變更符號** ] 對話方塊，可讓您變更符號的名稱或值。<br/><br/>如果符號用於使用中的控制項或資源，只可以從對應的資源編輯器變更符號。 如需詳細資訊，請參閱 [管理符號](./changing-a-symbol-or-symbol-name-id.md)。|
|**檢視使用**|開啟在對應資源編輯器中含有符號的資源。|

## <a name="create-symbols"></a>建立符號

### <a name="to-create-a-new-symbol"></a>建立新的符號

1. 在 [ **資源符號** ] 對話方塊中，選擇 [ **新增**]。

1. 在 [ **名稱** ] 方塊中，輸入符號名稱。

1. 接受指派的符號值，或在 [ **值** ] 方塊中輸入新值。

1. 選取 **[確定]** ，將新符號加入符號清單中。

> [!NOTE]
> 如果您輸入的符號名稱已經存在，此時會出現訊息方塊，說明已定義使用該名稱的符號。 您無法使用相同的名稱來定義兩個或多個符號，但您可以使用相同的數值來定義不同的符號。

## <a name="to-view-resource-symbols"></a>檢視資源符號

在 [資源檢視](how-to-create-a-resource-script-file.md#create-resources)中，以滑鼠右鍵按一下 *.rc* 檔，然後選取 [ **資源** 符號]，以在 [ **資源符號** ] 對話方塊中查看資源符號表。

> [!NOTE]
> 若要查看預先定義的符號，請核取 [ **顯示唯讀符號** ] 核取方塊。

### <a name="to-open-the-resource-editor-for-a-given-symbol"></a>開啟指定符號的資源編輯器

當您流覽 **資源符號**中的符號時，您可能會想要瞭解如何使用特定符號的詳細資訊。 [ **View Use** ] 按鈕提供快速的方法來取得此資訊。

1. 在 [ **資源符號** ] 對話方塊的 [ **名稱** ] 方塊中，選取一個符號。

1. 在 [ **消費者** ] 方塊中，選取您感興趣的資源類型。

1. 選取 [ **View Use** ] 按鈕。

   資源會出現在適當的編輯器視窗中。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[ (符號的資源識別碼) ](../windows/symbols-resource-identifiers.md)<br/>
[如何：管理符號](../windows/changing-a-symbol-or-symbol-name-id.md)<br/>
[預先定義的符號 Id](../windows/predefined-symbol-ids.md)<br/>
