---
title: 鍵盤和滑鼠自訂
ms.date: 11/19/2018
helpviewer_keywords:
- customizations [MFC], keyboard and mouse (MFC Extensions)
- keyboard and mouse customizations (MFC Extensions)
ms.assetid: 1f789f1b-5f2e-4b11-b974-e3e2a2e49d82
ms.openlocfilehash: 55eaac9d800730f3a01dcdb2eef943eb48d147b1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62311143"
---
# <a name="keyboard-and-mouse-customization"></a>鍵盤和滑鼠自訂

MFC 可讓應用程式的使用者自訂處理鍵盤和滑鼠輸入的方式。 使用者可以藉由指派命令的鍵盤快速鍵自訂鍵盤輸入。 使用者也可以選取在特定應用程式視窗中按兩下時應執行的命令，藉此自訂滑鼠輸入。 本主題將說明如何自訂應用程式的輸入。

在 [**自訂**] 對話方塊中，使用者可以變更滑鼠和鍵盤的自訂控制項。 若要顯示此對話方塊中，使用者會指向**自訂**上**檢視**功能表，然後按一下**工具列和停駐**。 在對話方塊中，使用者會按一下其中一個**鍵盤**索引標籤或**滑鼠** 索引標籤。

## <a name="keyboard-customization"></a>鍵盤自訂

如下圖所示**鍵盤**索引標籤**自訂** 對話方塊。

![在 [自訂] 對話方塊的 [鍵盤] 索引標籤](../mfc/media/mfcnextkeyboardtab.png "自訂 對話方塊中的 [鍵盤] 索引標籤") <br/>
鍵盤自訂索引標籤

使用者可與 [鍵盤] 索引標籤互動，將一個或多個鍵盤快速鍵指派給命令。 索引標籤左側會列出可用的命令。使用者可以從功能表中選取所有可用的命令。 但是只有功能表命令可以與鍵盤快速鍵相關聯。 在使用者輸入新的快速鍵之後**指派**按鈕即變成啟用。 當使用者按一下這個按鈕時，應用程式就會將選取的命令與該捷徑產生關聯。

所有目前指派的鍵盤快速鍵都會在右欄的清單方塊中列出。 使用者也可以選取個別快速鍵並將它們移除，或是重設應用程式的所有對應。

如果您想要在您的應用程式中支援這項自訂，您必須建立[CKeyboardManager](../mfc/reference/ckeyboardmanager-class.md)物件。 若要建立`CKeyboardManager`物件，請呼叫此函式[CWinAppEx::InitKeyboardManager](../mfc/reference/cwinappex-class.md#initkeyboardmanager)。 這個方法會建立並初始化鍵盤管理員。 即使您手動建立鍵盤管理員，仍然必須呼叫 `CWinAppEx::InitKeyboardManager` 將它初始化。

如果您使用精靈來建立應用程式，精靈將會初始化鍵盤管理員。 您的應用程式初始化鍵盤管理員之後，架構會將**鍵盤**tab 鍵移至**自訂** 對話方塊。

## <a name="mouse-customization"></a>滑鼠自訂

如下圖所示**滑鼠**索引標籤**自訂** 對話方塊。

![在 [自訂] 對話方塊中 [滑鼠] 索引標籤](../mfc/media/mfcnextmousetab.png "滑鼠 索引標籤中 [自訂] 對話方塊") <br/>
滑鼠自訂索引標籤

使用者可與這個索引標籤互動，以指派按兩下滑鼠動作的功能表命令。 使用者從視窗左側選取一個檢視，然後使用右側的控制項將命令與按兩下動作產生關聯。 在使用者按下**關閉**，每當使用者的任何位置按兩下檢視中，應用程式會執行相關聯的命令。

根據預設，當您使用精靈建立應用程式時，滑鼠自訂不會啟用。

#### <a name="to-enable-mouse-customization"></a>啟用滑鼠自訂

1. 初始化[CMouseManager](../mfc/reference/cmousemanager-class.md)藉由呼叫物件[CWinAppEx::InitMouseManager](../mfc/reference/cwinappex-class.md#initmousemanager)。

1. 取得滑鼠管理員的指標，使用[CWinAppEx::GetMouseManager](../mfc/reference/cwinappex-class.md#getmousemanager)。

1. 使用將檢視加入至滑鼠管理員[CMouseManager::AddView](../mfc/reference/cmousemanager-class.md#addview)方法。 針對您要加入至滑鼠管理員的每個檢視執行這項作業。

您的應用程式初始化滑鼠管理員之後，架構會將**滑鼠**tab 鍵移至**自訂** 對話方塊。 如果您未加入任何檢視，則存取這個索引標籤將會產生未處理的例外狀況。 建立一份檢視之後,**滑鼠** 索引標籤會提供給使用者。

當您將新的檢視加入至滑鼠管理員時，會指定該檢視的唯一 ID。 如果您想要視窗支援滑鼠自訂，您必須處理 WM_LBUTTONDBLCLICK 訊息並呼叫[CWinAppEx::OnViewDoubleClick](../mfc/reference/cwinappex-class.md#onviewdoubleclick)函式。 當您呼叫這個函式時，其中一個參數會是該視窗的 ID。 程式設計人員必須責任追蹤 ID 編號以及與其相關聯的物件。

## <a name="security-concerns"></a>安全性考量

中所述[使用者定義工具](../mfc/user-defined-tools.md)，使用者可以建立使用者定義工具 ID 與按兩下事件的關聯。 當使用者按兩下檢視時，應用程式會尋找符合相關聯 ID 的使用者工具。 如果應用程式找到相符的工具，就會執行該工具。 如果應用程式找不到符合的工具，則會傳送包含該 ID 的 WM_COMMAND 訊息至按兩下的檢視。

自訂的設定會儲存在登錄中。 透過編輯登錄，攻擊者就可以用任意命令取代有效的使用者工具 ID。 當使用者按兩下檢視時，檢視就會處理攻擊者植入的命令。 這樣可能會造成無法預期且具有潛在危險性的行為。

此外，這種攻擊可能會避開使用者介面的保護。 例如，假設應用程式已停用列印。 也就是在其使用者介面**列印**功能表和按鈕都無法使用。 通常這樣會防止應用程式進行列印。 但是，如果攻擊者編輯登錄，使用者就可以直接透過按兩下檢視的方式傳送列印命令，而避開無法使用的使用者介面項目。

為了防範這種攻擊，在執行命令之前，請在應用程式命令處理常式中加入程式碼以驗證命令是否有效。 不要倚賴使用者介面阻止命令傳送至應用程式。

## <a name="see-also"></a>另請參閱

[MFC 自訂](../mfc/customization-for-mfc.md)<br/>
[CKeyboardManager 類別](../mfc/reference/ckeyboardmanager-class.md)<br/>
[CMouseManager 類別](../mfc/reference/cmousemanager-class.md)<br/>
[自訂的安全性影響](../mfc/security-implications-of-customization.md)
