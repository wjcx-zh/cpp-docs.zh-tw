---
title: 以手動方式加入控制項
ms.date: 11/04/2016
helpviewer_keywords:
- Windows common controls [MFC], adding
- dialog box controls [MFC], adding to dialog boxes
- controlling input focus
- input focus control
- focus, controlling input [MFC]
- controls [MFC], adding to dialog boxes
- common controls [MFC], adding
ms.assetid: bc843e59-0c51-4b5b-8bf2-343f716469d2
ms.openlocfilehash: 4efd1c23c7e4d6f7d8e6fa9fe046f8de11c825a6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626528"
---
# <a name="adding-controls-by-hand"></a>以手動方式加入控制項

您可以使用[對話方塊編輯器將控制項加入至對話方塊](using-the-dialog-editor-to-add-controls.md)，或使用程式碼自行加入。

若要自行建立控制項物件，您通常會在 c + + 對話方塊或框架視窗物件中內嵌 c + + 控制項物件。 就像架構中的許多其他物件一樣，控制項也需要兩階段式的結構。 您應該呼叫控制項的**Create**成員函式，做為建立父對話方塊或框架視窗的一部分。 在對話方塊中，這通常是在[OnInitDialog](reference/cdialog-class.md#oninitdialog)中完成，而針對框架視窗則是在[OnCreate](reference/cwnd-class.md#oncreate)中進行。

下列範例會示範如何在 `CEdit` 衍生對話方塊類別的類別宣告中宣告物件，然後在中呼叫成員函式 `Create` `OnInitDialog` 。 因為 `CEdit` 物件宣告為内嵌物件，所以會在構造對話方塊物件時自動加以建立，但仍必須使用自己的成員函式來初始化 `Create` 。

[!code-cpp[NVC_MFCControlLadenDialog#1](codesnippet/cpp/adding-controls-by-hand_1.h)]

下列函式會 `OnInitDialog` 設定一個矩形，然後呼叫 `Create` 以建立 Windows 編輯控制項，並將它附加至未初始化的 `CEdit` 物件。

[!code-cpp[NVC_MFCControlLadenDialog#2](codesnippet/cpp/adding-controls-by-hand_2.cpp)]

建立 edit 物件之後，您也可以藉由呼叫成員函式，將輸入焦點設定為控制項 `SetFocus` 。 最後，您會從傳回0， `OnInitDialog` 以顯示您設定焦點。 如果您傳回非零值，對話方塊管理員會將焦點設定為對話方塊專案清單中的第一個控制項專案。 在大部分的情況下，您會想要使用對話方塊編輯器，將控制項加入對話方塊中。

## <a name="see-also"></a>另請參閱

[建立及使用控制項](making-and-using-controls.md)<br/>
[控制項](controls-mfc.md)<br/>
[CDialog：： OnInitDialog](reference/cdialog-class.md#oninitdialog)
