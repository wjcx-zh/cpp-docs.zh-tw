---
title: ActiveX 控制項容器：在 ActiveX 控制項容器中程式設計 ActiveX 控制項
ms.date: 09/12/2018
helpviewer_keywords:
- ActiveX control containers [MFC], accessing ActiveX controls
- Confirm Classes dialog box
- wrapper classes [MFC], ActiveX controls
- ActiveX control containers [MFC], wrapper classes
- ActiveX controls [MFC], accessing
- MFC ActiveX controls [MFC], accessing in containers
- header files [MFC], for ActiveX control wrapper class
- wrapper classes [MFC], using
- ActiveX controls [MFC], wrapper classes
ms.assetid: ef9b2480-92d6-4191-b16e-8055c4fd7b73
ms.openlocfilehash: 9620f4d47197147db4972c9f2024f6018a705902
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371193"
---
# <a name="activex-control-containers-programming-activex-controls-in-an-activex-control-container"></a>ActiveX 控制項容器：在 ActiveX 控制項容器中程式設計 ActiveX 控制項

本文介紹了存取嵌入式 ActiveX 控制項的公開[方法和](../mfc/mfc-activex-controls-methods.md)[屬性](../mfc/mfc-activex-controls-properties.md)的過程。

>[!IMPORTANT]
> ActiveX 是一種不應用於新開發的傳統技術。 有關取代 ActiveX 的現代技術的詳細資訊,請參閱[ActiveX 控制件](activex-controls.md)。

基本上,您將按照以下步驟操作:

1. 使用函式[庫將 ActiveX 控制檔插入到 ActiveX 容器項目中](../mfc/inserting-a-control-into-a-control-container-application.md)。

1. [定義與](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md)ActiveX 控件包裝類類型相同的成員變數(或其他形式的訪問)。

1. 使用包裝類別的預先定義成員函數[, 對 ActiveX 控制檔 。](#_core_programming_the_activex_control)

對於此討論,假設您創建了一個基於對話框的專案(名為容器),支援 ActiveX 控件。 Circ 樣本控制,Circ,將添加到生成的專案中。

將 Circ 控制項插入到專案(步驟 1)後,將 Circ 控制項的實例插入到應用程式的主對話框中。

## <a name="procedures"></a>程序

#### <a name="to-add-the-circ-control-to-the-dialog-template"></a>新增的 Circ 控制檔到對話框樣本

1. 載入 ActiveX 控制容器專案。 這個選項, 請使用專案`Container`。

1. 按下「資源檢視」選項卡。

1. 打開**對話框**資料夾。

1. 按兩下主對話方塊範本。 這個範例, 請使用**IDD_CONTAINER_DIALOG**。

1. 按一下工具箱上的 Circ 控制件圖示。

1. 按一下對話框中的一個點以插入 Circ 控制項。

1. 在 **「檔」** 選單中,選擇 **「全部儲存」** 以儲存對對話方塊樣本的所有修改。

## <a name="modifications-to-the-project"></a>變更項目的變更

為了使容器應用程式能夠造訪 Circ 控制項,Visual C++`CCirc`自動添加包裝類 () 實現檔 (。CPP)到容器專案和包裝類標頭 (。H) 檔案到對話框標頭檔:

[!code-cpp[NVC_MFC_AxCont#1](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_1.h)]

## <a name="the-wrapper-class-header-h-file"></a><a name="_core_the_wrapper_class_header_28h29_file"></a>包裝類標頭 (.H) 檔案

要取得與設定 Circ 控制的屬性(和呼叫方法),`CCirc`包裝類提供所有公開方法和屬性的聲明。 在此示例中,這些聲明見於中國保監會。H。 以下範例是定義 ActiveX`CCirc`控制項公開介面的類別部分:

[!code-cpp[NVC_MFC_AxCont#2](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_2.h)]
[!code-cpp[NVC_MFC_AxCont#3](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_3.h)]

然後,可以使用正常的C++語法從應用程式的其他過程調用這些函數。 有關使用此成員函數集存取控制項的方法和屬性的詳細資訊,請參閱[程式設計 ActiveX 控制件](#_core_programming_the_activex_control)的部分。

## <a name="member-variable-modifications-to-the-project"></a><a name="_core_member_variable_modifications_to_the_project"></a>對項目的成員變數修改

將 ActiveX 控制件添加到專案中並嵌入到對話方塊容器中後,專案的其他部分可以存取它。 訪問控制項的最簡單方法是建立對話方塊`CContainerDlg`類[的成員變數](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md)(步驟 2),該變數的類型與 Visual C++添加到專案的包裝類類型相同。 然後,您可以隨時使用成員變數訪問嵌入控制項。

當 **「新增成員變數」** 對話框將*m_circctl*成員變數添加到專案中時,它還向標頭檔 () 添加以下行。H)`CContainerDlg`類別:

[!code-cpp[NVC_MFC_AxCont#4](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_4.h)]
[!code-cpp[NVC_MFC_AxCont#5](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_5.h)]

此外,對**DDX_Control**的調用會自動添加到`CContainerDlg`的實現中: `DoDataExchange`

[!code-cpp[NVC_MFC_AxCont#6](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_6.cpp)]

## <a name="programming-the-activex-control"></a><a name="_core_programming_the_activex_control"></a>程式設計 ActiveX 控制項

此時,您已將 ActiveX 控制項插入到對話方塊樣本中,並為其創建了一個成員變數。 現在可以使用常用C++語法來訪問嵌入控制項的屬性和方法。

如前所述(在[包裝類標題(中)。H) 檔案](#_core_the_wrapper_class_header_28h29_file)),標頭檔 (。H)`CCirc`包裝 類,在這種情況下,中國保監會。H,包含可用於獲取和設置任何公開屬性值的成員函數的清單。 公開方法的成員函數也可用。

修改控制項屬性的常見位置位於主對話框類`OnInitDialog`的成員函數中。 此函數在對話框出現之前調用,用於初始化其內容,包括其任何控制項。

以下代碼範例使用*m_circctl*成員變數修改嵌入式 Circ 控制項的標題和 CircleShape 屬性:

[!code-cpp[NVC_MFC_AxCont#7](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_7.cpp)]

## <a name="see-also"></a>另請參閱

[ActiveX 控制項容器](../mfc/activex-control-containers.md)
