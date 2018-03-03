---
title: "ActiveX 控制項容器： 程式設計 ActiveX 控制項容器中的 ActiveX 控制項 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5a608d98b43e6daf340ab09c7adb275849f347a2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="activex-control-containers-programming-activex-controls-in-an-activex-control-container"></a>ActiveX 控制項容器：在 ActiveX 控制項容器中程式設計 ActiveX 控制項
本文說明的程序存取公開[方法](../mfc/mfc-activex-controls-methods.md)和[屬性](../mfc/mfc-activex-controls-properties.md)內嵌 ActiveX 控制項。 基本上，您會執行下列步驟：  
  
1.  [ActiveX 控制項插入 ActiveX 容器專案](../mfc/inserting-a-control-into-a-control-container-application.md)使用組件庫。  
  
2.  [定義的成員變數](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md)（或其他形式的存取） 的相同的型別 ActiveX 控制項 包裝函式類別。  
  
3.  [程式 ActiveX 控制項](#_core_programming_the_activex_control)使用預先定義的包裝函式類別成員函式。  
  
 本討論中，假設您已建立對話方塊架構的專案 （名為容器） 的 ActiveX 控制項支援。 Circ 控制項範例，Circ，將會加入至產生的專案。  
  
 一旦 Circ 控制項插入至專案 （步驟 1），請將 Circ 控制項的執行個體插入至主應用程式的對話方塊。  
  
## <a name="procedures"></a>程序  
  
#### <a name="to-add-the-circ-control-to-the-dialog-template"></a>若要將 Circ 控制項加入至對話方塊範本  
  
1.  載入的 ActiveX 控制項容器專案。 此範例中，使用`Container`專案。  
  
2.  按一下 [資源檢視] 索引標籤。  
  
3.  開啟**對話方塊**資料夾。  
  
4.  按兩下主要對話方塊範本。 此範例中，使用**IDD_CONTAINER_DIALOG**。  
  
5.  按一下工具箱上的 Circ 控制項圖示。  
  
6.  按一下以插入 Circ 控制項在對話方塊內的位置。  
  
7.  從**檔案**功能表上，選擇**全部儲存**儲存對話方塊範本的所有修改。  
  
## <a name="modifications-to-the-project"></a>修改專案  
 若要啟用存取 Circ 控制項容器應用程式，Visual c + + 會自動加入包裝函式類別 (`CCirc`) 實作檔 (。CPP) 加入容器專案，並包裝函式類別標頭 (。H） 檔案至對話方塊的方塊標頭檔：  
  
 [!code-cpp[NVC_MFC_AxCont#1](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_1.h)]  
  
##  <a name="_core_the_wrapper_class_header_28h29_file"></a>包裝函式類別標頭 (。H） 檔案  
 若要取得和設定屬性 （叫用方法） Circ 控制項，`CCirc`包裝函式提供的所有公開的方法和屬性的宣告。 在範例中，這些宣告位於變動圓形H. 下列範例是類別的部分`CCirc`定義公開的介面的 ActiveX 控制項：  
  
 [!code-cpp[NVC_MFC_AxCont#2](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_2.h)]  
[!code-cpp[NVC_MFC_AxCont#3](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_3.h)]  
  
 然後可以從其他應用程式的程序使用標準 c + + 語法呼叫這些函式。 如需有關如何使用這個成員函式，以存取控制項的方法和屬性的詳細資訊，請參閱下節[程式設計 ActiveX 控制項](#_core_programming_the_activex_control)。  
  
##  <a name="_core_member_variable_modifications_to_the_project"></a>成員變數修改專案  
 當 ActiveX 控制項已加入至專案，而且內嵌在對話方塊容器中時，它可以存取專案的其他組件。 最簡單的方式來存取控制項是[建立成員變數](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md)對話方塊類別的`CContainerDlg`（步驟 2），也就是包裝函式類別加入至專案，Visual c + + 類型相同。 成員變數，然後可用來存取內嵌的控制項，在任何時間。  
  
 當**加入成員變數**對話方塊新增`m_circctl`成員變數加入專案時，它也會加入下列幾行至標頭檔 (。H） 的`CContainerDlg`類別：  
  
 [!code-cpp[NVC_MFC_AxCont#4](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_4.h)]  
[!code-cpp[NVC_MFC_AxCont#5](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_5.h)]  
  
 此外，呼叫**DDX_Control**會自動加入至`CContainerDlg`的實作`DoDataExchange`:  
  
 [!code-cpp[NVC_MFC_AxCont#6](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_6.cpp)]  
  
##  <a name="_core_programming_the_activex_control"></a>程式設計 ActiveX 控制項  
 此時，您有對話方塊範本中插入 ActiveX 控制項，並為它建立成員變數。 您現在可以使用通用的 c + + 語法來存取的屬性和內嵌控制項的方法。  
  
 如所述 (在[包裝函式類別標頭 (。H） 檔](#_core_the_wrapper_class_header_28h29_file))，標頭檔 (。H） 如`CCirc`包裝函式類別，在此案例的變動圓形H、 包含您可用來取得和設定任何公開的屬性值的成員函式的清單。 成員函式公開的方法也會提供。  
  
 若要修改控制項屬性的一般位置是在`OnInitDialog`主對話方塊類別成員函式。 對話方塊隨即出現，用來初始化它的內容，包括其控制項之前呼叫此函式。  
  
 下列程式碼範例使用`m_circctl`成員變數，以修改內嵌 Circ 控制項的標題和 CircleShape 屬性：  
  
 [!code-cpp[NVC_MFC_AxCont#7](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_7.cpp)]  
  
## <a name="see-also"></a>請參閱  
 [ActiveX 控制項容器](../mfc/activex-control-containers.md)

