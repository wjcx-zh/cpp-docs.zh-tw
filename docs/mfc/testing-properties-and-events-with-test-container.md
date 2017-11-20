---
title: "使用測試容器測試屬性和事件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- testing, test containers
- tstcon32.exe
- debugging ActiveX controls
- test container
- ActiveX Control Test Container
- ActiveX controls [MFC], testing
- properties [MFC], testing
ms.assetid: 626867cf-fe53-4c30-8973-55bb93ef3917
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 88b1240666c15601f4a003d0d021fd12dc039fe1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="testing-properties-and-events-with-test-container"></a>使用測試容器測試屬性和事件
隨附於 Visual C++ 的 Test Container 應用程式是一個 ActiveX 控制項容器，用於測試和偵錯 ActiveX 控制項。 Test Container 可讓控制項開發人員藉由變更其屬性、叫用其方法和引發其事件來測試控制項的功能。 Test Container 可以顯示資料繫結通知的記錄，並提供測試 ActiveX 控制項永續性的功能：您可以將屬性儲存至資料流或到子儲存區、重新載入它們以及檢查已儲存的資料流資料。 本節說明如何使用 Test Container 的基本功能。 如需詳細資訊，請選取**協助**功能表執行 Test Container 時。  
  
### <a name="to-access-the-activex-control-test-container"></a>存取 ActiveX 控制項測試容器  
  
1.  建置[TSTCON 範例： ActiveX 控制項測試容器](../visual-cpp-samples.md)。  
  
### <a name="to-test-your-activex-control"></a>測試您的 ActiveX 控制項  
  
1.  在**編輯**測試容器的功能表，按一下 **插入新控制項**。  
  
2.  在**插入控制項**，選取所要的控制項，然後按一下**確定**。 控制項隨即會出現在控制項容器中。  
  
    > [!NOTE]
    >  如果您的控制項未列在**插入控制項**對話方塊方塊中，請確定您已註冊使用**登錄控制項**命令**檔案**測試功能表容器。  
  
 現在您可以測試控制項的屬性或事件。  
  
#### <a name="to-test-properties"></a>測試屬性  
  
1.  在**控制項**功能表上，按一下 **叫用方法**。  
  
2.  在**方法名稱**下拉式清單中，選取您想要測試的屬性的 PropPut 方法。  
  
3.  修改**參數值**或**參數型別**，然後按一下 [**設定值**] 按鈕。  
  
4.  按一下**Invoke**来套用至物件的新值。  
  
     屬性現在會包含新的值。  
  
#### <a name="to-test-events-and-specify-the-destination-of-event-information"></a>若要測試事件和指定事件資訊的目的地。  
  
1.  在**選項**功能表上，按一下 **記錄**。  
  
2.  指定事件資訊的目的地。  
  
## <a name="see-also"></a>另請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   
 [如何：偵錯 ActiveX 控制項](/visualstudio/debugger/how-to-debug-an-activex-control)

