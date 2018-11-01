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
ms.openlocfilehash: c9a0c51d090b1c62309f27bf6587ea02e0fe1152
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636887"
---
# <a name="activex-control-containers-programming-activex-controls-in-an-activex-control-container"></a>ActiveX 控制項容器：在 ActiveX 控制項容器中程式設計 ActiveX 控制項

這篇文章說明公開存取的程序[方法](../mfc/mfc-activex-controls-methods.md)並[屬性](../mfc/mfc-activex-controls-properties.md)內嵌 ActiveX 控制項。

>[!IMPORTANT]
> ActiveX 是舊版的技術，不應用於新的開發。 如需有關取代 ActiveX 的現代技術的詳細資訊，請參閱[ActiveX 控制項](activex-controls.md)。

基本上，您將會遵循下列步驟：

1. [插入 ActiveX 容器專案中的 ActiveX 控制項](../mfc/inserting-a-control-into-a-control-container-application.md)使用資源庫。

1. [定義的成員變數](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md)（或其他形式的存取） 相同的型別為 ActiveX 控制項包裝函式類別。

1. [ActiveX 控制項進行程式設計](#_core_programming_the_activex_control)使用預先定義的包裝函式類別的成員函式。

在本文中，假設您已建立對話方塊架構的專案 （名為容器） 與 ActiveX 控制項支援。 Circ 控制項範例，圓形，會將產生的專案。

一旦 Circ 控制項插入至專案 （步驟 1），插入應用程式的主要對話方塊 Circ 控制項的執行個體。

## <a name="procedures"></a>程序

#### <a name="to-add-the-circ-control-to-the-dialog-template"></a>若要將 Circ 控制項新增至對話方塊範本

1. 載入 ActiveX 控制項容器專案。 此範例中，使用`Container`專案。

1. 按一下 [資源檢視] 索引標籤。

1. 開啟** 對話方塊**資料夾。

1. 按兩下主要對話方塊範本。 此範例中，使用**IDD_CONTAINER_DIALOG**。

1. 按一下工具箱上的 Circ 控制項圖示。

1. 按一下以插入 Circ 控制項 對話方塊中的位置。

1. 從**檔案**功能表上，選擇**全部儲存**儲存對話方塊範本的所有修改。

## <a name="modifications-to-the-project"></a>修改專案

若要啟用存取 Circ 控制項容器應用程式，Visual c + + 會自動加入包裝函式類別 (`CCirc`) 實作檔 (。CPP) 容器專案到包裝函式類別標頭 (。H） 對話方塊的方塊標頭檔的檔案：

[!code-cpp[NVC_MFC_AxCont#1](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_1.h)]

##  <a name="_core_the_wrapper_class_header_28h29_file"></a> 包裝函式類別標頭 (。H） 檔案

若要取得和設定屬性 （叫用方法） Circ 控制項，`CCirc`包裝函式提供的所有公開的方法和屬性的宣告。 在範例中，這些宣告位於變動圓形H. 下列範例是類別的部分`CCirc`定義公開的介面，ActiveX 控制項：

[!code-cpp[NVC_MFC_AxCont#2](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_2.h)]
[!code-cpp[NVC_MFC_AxCont#3](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_3.h)]

然後可以從其他使用一般的 c + + 語法的應用程式的程序呼叫這些函式。 如需有關如何使用此設定為存取控制的方法和屬性的成員函式的詳細資訊，請參閱下節[程式設計 ActiveX 控制項](#_core_programming_the_activex_control)。

##  <a name="_core_member_variable_modifications_to_the_project"></a> 成員變數修改專案

一旦已經加入至專案並內嵌在對話方塊容器中的 ActiveX 控制項，即可存取專案的其他部分。 存取控制的最簡單方式是[建立成員變數](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md)的對話方塊類別中， `CContainerDlg` （步驟 2），也就是加入至專案，Visual c + + 包裝函式類別類型相同。 成員變數，然後可用來存取內嵌的控制項，在任何時間。

當**加入成員變數** 對話方塊中加入*m_circctl*成員變數加入專案，也會增加下列幾行的標頭檔 (。H） 的`CContainerDlg`類別：

[!code-cpp[NVC_MFC_AxCont#4](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_4.h)]
[!code-cpp[NVC_MFC_AxCont#5](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_5.h)]

此外，呼叫**DDX_Control**會自動新增至`CContainerDlg`的實作`DoDataExchange`:

[!code-cpp[NVC_MFC_AxCont#6](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_6.cpp)]

##  <a name="_core_programming_the_activex_control"></a> 程式設計 ActiveX 控制項

此時，您有對話方塊範本中插入 ActiveX 控制項，並為它建立成員變數。 您現在可以使用一般的 c + + 語法來存取的屬性和內嵌控制項的方法。

如所述 (在[的包裝函式類別標頭 (。H） 檔案](#_core_the_wrapper_class_header_28h29_file))，標頭檔 (。H） 針對`CCirc`包裝函式類別，在此案例的變動圓形H、 包含您可用來取得和設定任何公開的屬性值的成員函式的清單。 成員函式公開的方法也會提供。

若要修改的控制項屬性的常見位置是在`OnInitDialog`主對話方塊類別成員函式。 對話方塊隨即出現，用來初始化它的內容，包括任何它的控制項時之前，會呼叫此函數。

下列程式碼範例會使用*m_circctl*修改內嵌 Circ 控制項的標題和 CircleShape 屬性的成員變數：

[!code-cpp[NVC_MFC_AxCont#7](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_7.cpp)]

## <a name="see-also"></a>另請參閱

[ActiveX 控制項容器](../mfc/activex-control-containers.md)

