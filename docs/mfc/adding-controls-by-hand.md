---
title: 加入控制項以手動方式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows common controls [MFC], adding
- dialog box controls [MFC], adding to dialog boxes
- controlling input focus
- input focus control
- focus, controlling input [MFC]
- controls [MFC], adding to dialog boxes
- common controls [MFC], adding
ms.assetid: bc843e59-0c51-4b5b-8bf2-343f716469d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 72170e3e21f5ca895b95da0d5905a2167375f721
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46434540"
---
# <a name="adding-controls-by-hand"></a>以手動方式加入控制項

您可以[將控制項加入對話方塊中，使用對話方塊編輯器](../mfc/using-the-dialog-editor-to-add-controls.md)或將其新增您自己，使用程式碼。

若要建立您自己的控制項物件，您通常會內嵌在 c + + 對話方塊中的 c + + 控制項物件或框架視窗物件。 Framework 中其他許多物件，例如控制項需要兩階段建構。 您應該呼叫控制項的**建立**成員函式，建立父對話方塊或框架視窗的過程。 對話方塊中，這通常是[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)，以及框架視窗中[OnCreate](../mfc/reference/cwnd-class.md#oncreate)。

下列範例示範您可以宣告`CEdit`在類別宣告中的衍生的對話方塊類別的物件，然後呼叫`Create`成員函式中的`OnInitDialog`。 因為`CEdit`物件宣告為內嵌物件，它會自動建構對話方塊物件建構後，但仍然必須予以初始化有其專屬`Create`成員函式。

[!code-cpp[NVC_MFCControlLadenDialog#1](../mfc/codesnippet/cpp/adding-controls-by-hand_1.h)]

下列`OnInitDialog`函式中設定一個矩形，然後呼叫`Create`建立 Windows 編輯控制項，並將它附加至未初始化`CEdit`物件。

[!code-cpp[NVC_MFCControlLadenDialog#2](../mfc/codesnippet/cpp/adding-controls-by-hand_2.cpp)]

建立編輯物件之後，您也可以設定輸入的焦點控制藉由呼叫`SetFocus`成員函式。 最後，您可以傳回從 0`OnInitDialog`以顯示您將焦點設定。 如果要傳回非零值時，對話方塊管理員會將焦點設定在對話方塊的 [項目] 清單中的第一個控制項項目。 在大部分情況下，您會想要將控制項新增至您的對話方塊中，使用對話方塊編輯器。

## <a name="see-also"></a>另請參閱

[建立及使用控制項](../mfc/making-and-using-controls.md)<br/>
[控制項](../mfc/controls-mfc.md)<br/>
[CDialog::OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)

