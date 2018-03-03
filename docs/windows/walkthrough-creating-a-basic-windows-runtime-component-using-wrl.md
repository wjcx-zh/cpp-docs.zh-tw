---
title: "逐步解說： 建立基本 Windows 執行階段元件使用 WRL |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: 6e3f0986-7905-4f94-90e5-22c2ebfc8cd0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5859f3ebfcb55427e239a0018d539e2f4df13800
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-creating-a-basic-windows-runtime-component-using-wrl"></a>逐步解說：使用 WRL 建立基本 Windows 執行階段元件
本文件說明如何使用 Windows 執行階段 c + + 樣板程式庫 (WRL) 來建立基本 Windows 執行階段元件。 元件會將兩個數字相加，結果為質數時引發事件。 本文件也會示範如何從使用 JavaScript 之通用 Windows 平台應用程式使用元件。  
  
## <a name="prerequisites"></a>必要條件  
  
-   體驗[Windows 執行階段](http://msdn.microsoft.com/library/windows/apps/br211377.aspx)。  
  
-   COM 的體驗。  
  
### <a name="to-create-a-basic-windows-runtime-component-that-adds-two-numbers"></a>若要建立兩個數目相加的基本 Windows 執行階段元件  
  
1.  在 Visual Studio 中建立 Visual c + +`WRLClassLibrary`專案。 文件[類別庫專案範本](../windows/wrl-class-library-project-template.md)說明如何下載這個範本。 將專案命名為 `Contoso`。  
  
2.  在 Contoso.cpp 和 Contoso.idl，取代"WinRTClass 」 與 「 計算機 」 的所有執行個體。  
  
3.  在 Contoso.idl，加入`Add`方法`ICalculator`介面。  
  
     [!code-cpp[wrl-basic-component#1](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_1.idl)]  
  
4.  在 Contoso.cpp，加入`Add`方法`public`區段`Calculator`類別。  
  
     [!code-cpp[wrl-basic-component#2](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_2.cpp)]  
  
    > [!IMPORTANT]
    >  因為您要建立 COM 元件，請務必使用`__stdcall`呼叫慣例。  
  
     我們建議您改用`_Out_`和其他來源註釋語言 (SAL) 註釋說明函式如何使用它的參數。 SAL 註釋也可描述傳回值。 SAL 註釋可搭配[C/c + + 程式碼分析工具](/visualstudio/code-quality/code-analysis-for-c-cpp-overview)來尋找 C 和 c + + 中可能的缺失原始程式碼。 工具所報告的常見程式碼撰寫錯誤包括緩衝區滿溢、 未初始化的記憶體、 null 指標取值以及記憶體和資源流失。  
  
### <a name="to-use-the-component-from-a-universal-windows-platform-app-that-uses-javascript"></a>若要使用從使用 JavaScript 之通用 Windows 平台應用程式元件  
  
1.  在 Visual Studio 中，加入新的 JavaScript`Blank App`專案加入`Contoso`方案。 將專案命名為 `CalculatorJS`。  
  
2.  在`CalculatorJS`專案中，將參考加入`Contoso`專案。  
  
3.  在 default.html，將取代`body`區段這些 UI 項目：  
  
     [!code-html[wrl-basic-component#3](../windows/codesnippet/Html/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_3.html)]  
  
4.  在 default.js 中實作`OnClick`函式。  
  
     [!code-javascript[wrl-basic-component#4](../windows/codesnippet/JavaScript/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_4.js)]  
  
    > [!NOTE]
    >  在 JavaScript 中，方法名稱的第一個字母會變更為小寫，以符合標準的命名慣例。  
  
### <a name="to-add-an-event-that-fires-when-a-prime-number-is-calculated"></a>若要加入質數計算時，就會引發事件  
  
1.  Contoso.idl 之前的宣告, 中`ICalculator`，定義委派類型， `PrimeNumberEvent`，這樣會提供`int`引數。  
  
     [!code-cpp[wrl-basic-component#5](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_5.idl)]  
  
     當您使用`delegate`關鍵字，MIDL 編譯器建立一個介面，包含`Invoke`該委派的簽章相符的方法。 在此範例中，所產生的檔案 Contoso_h.h 定義`IPrimeNumberEvent`介面，以便稍後用於此程序。  
  
     [!code-cpp[wrl-basic-component#13](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_6.cpp)]  
  
2.  在`ICalculator`介面，定義`PrimeNumberFound`事件。 `eventadd`和`eventremove`屬性指定的取用者`ICalculator`介面可訂閱和取消訂閱此事件。  
  
     [!code-cpp[wrl-basic-component#6](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_7.idl)]  
  
3.  在 Contoso.cpp，加入`private` [Microsoft::WRL::EventSource](../windows/eventsource-class.md)成員變數，來管理事件訂閱者，並叫用此事件處理常式。  
  
     [!code-cpp[wrl-basic-component#7](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_8.cpp)]  
  
4.  在 Contoso.cpp，實作`add_PrimeNumberFound`和`remove_PrimeNumberFound`方法。  
  
     [!code-cpp[wrl-basic-component#8](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_9.cpp)]  
  
### <a name="to-raise-the-event-when-a-prime-number-is-calculated"></a>引發事件會在計算質數時  
  
1.  在 Contoso.cpp，加入`IsPrime`方法`private`區段`Calculator`類別。  
  
     [!code-cpp[wrl-basic-component#12](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_10.cpp)]  
  
2.  修改`Calculator`的`Add`方法呼叫[Microsoft::WRL::EventSource::InvokeAll](../windows/eventsource-invokeall-method.md)質數計算後的方法。  
  
     [!code-cpp[wrl-basic-component#11](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_11.cpp)]  
  
### <a name="to-handle-the-event-from-javascript"></a>若要處理來自 JavaScript 的事件  
  
1.  在 default.html，修改`body`一節，納入包含質數的文字區域。  
  
     [!code-html[wrl-basic-component#9](../windows/codesnippet/Html/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_12.html)]  
  
2.  在 default.js 中修改`Add`函式來處理`PrimeNumberFound`事件。 此事件處理常式會將質數附加至前一個步驟所定義的文字區域。  
  
     [!code-javascript[wrl-basic-component#10](../windows/codesnippet/JavaScript/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_13.js)]  
  
    > [!NOTE]
    >  在 JavaScript 中，事件名稱都會變更為小寫，並會在前面加上以 「 on 」 以符合標準的命名慣例。  
  
 下圖顯示基本計算機應用程式。  
  
 ![使用 JavaScript 的基本計算機應用程式](../windows/media/wrl_basic_component.png "WRL_Basic_Component")  
  
## <a name="next-steps"></a>後續步驟  
  
## <a name="see-also"></a>請參閱  
 [Windows 執行階段 c + + 樣板程式庫 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)   
 [類別庫專案範本](../windows/wrl-class-library-project-template.md)   
 [C/c + + 程式碼分析工具](/visualstudio/code-quality/code-analysis-for-c-cpp-overview)