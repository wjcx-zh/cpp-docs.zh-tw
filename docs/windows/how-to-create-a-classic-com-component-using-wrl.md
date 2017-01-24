---
title: "如何：使用 WRL 建立傳統 COM 元件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: 5efe7690-90d5-4c3c-9e53-11a14cefcb19
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 WRL 建立傳統 COM 元件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以使用 [!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)] ([!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]) 來建立基本的傳統 COM 元件，除了用於 [!INCLUDE[win8_appstore_long](../build/reference/includes/win8_appstore_long_md.md)] 應用程式外，還可使用於桌面應用程式。 若是建立 COM 元件，[!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 需要的程式碼可能比 ATL 少。 如需 COM 的子集， [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 支援，請參閱 [Windows 執行階段 c + + 樣板程式庫 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)。  
  
 本文件說明如何使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 來建立基本的 COM 元件。 雖然您可以使用最符合您需求的部署機制，這份文件也顯示註冊和使用桌面應用程式之 COM 元件的基本方法。  
  
### <a name="to-use-the-includecppwrlshorttokencppwrlshortmdmd-to-create-a-basic-classic-com-component"></a>使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 來建立基本的傳統 COM 元件  
  
1.  在 Visual Studio 中建立 **空白方案** 專案。 為專案命名，例如 `WRLClassicCOM`。  
  
2.  新增 **Win32 專案** 至方案。 為專案命名，例如 `CalculatorComponent`。 在 **應用程式設定** 索引標籤上，選取 **DLL**。  
  
3.  新增 **Midl 檔案 (.idl)** 專案的檔案。 為檔案命名，例如 `CalculatorComponent.idl`。  
  
4.  將此程式碼加入至 CalculatorComponent.idl：  
  
     [!code-cpp[wrl-classic-com-component#1](../windows/codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_1.idl)]  
  
5.  在 CalculatorComponent.cpp 中定義 `CalculatorComponent` 類別。  `CalculatorComponent` 類別繼承自 [Microsoft::WRL::RuntimeClass](../windows/runtimeclass-class.md)。 [Microsoft::WRL::RuntimeClassFlags \< ClassicCom>](../windows/runtimeclassflags-structure.md) 指定該類別衍生自 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509\(v=vs.85\).aspx) 而非 [IInspectable](http://msdn.microsoft.com/library/br205821\(v=vs.85\).aspx)。 (`IInspectable` 只有 [!INCLUDE[win8_appstore_short](../windows/includes/win8_appstore_short_md.md)] 應用程式元件。) `CoCreatableClass` 建立適用於函式之類的類別處理站 [CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615\(v=vs.85\).aspx)。  
  
     [!code-cpp[wrl-classic-com-component#2](../windows/codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_2.cpp)]  
  
6.  使用下列程式碼取代 dllmain.cpp 中的程式碼。 此檔案會定義 DLL 匯出函式。 這些函式會使用 [Microsoft::WRL::Module](../windows/module-class.md) 類別來管理模組的類別處理站。  
  
     [!code-cpp[wrl-classic-com-component#3](../windows/codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_3.cpp)]  
  
7.  新增 **模組定義檔 (.def)** 專案的檔案。 為檔案命名，例如 `CalculatorComponent.def`。 此檔案可將連結器命名為要匯出的函式名稱。  
  
8.  將此程式碼加入至 CalculatorComponent.def：  
  
     [!CODE [wrl-classic-com-component#4](../CodeSnippet/VS_Snippets_Misc/wrl-classic-com-component#4)]  
  
9. 將 runtimeobject.lib 加入至連結器列。 若要了解做法，請參閱 [。Lib 檔做為連結器輸入](../build/reference/dot-lib-files-as-linker-input.md)。  
  
### <a name="to-consume-the-com-component-from-a-desktop-app"></a>使用桌面應用程式的 COM 元件  
  
1.  使用 Windows 登錄註冊 COM 元件。 若要這樣做，請建立登錄項目檔案，其命名為 `RegScript.reg`, ，並加入下列文字。 取代 *\< dll 路徑 >* 之 DLL 的路徑，例如 `C:\\temp\\WRLClassicCOM\\Debug\\CalculatorComponent.dll`。  
  
     [!CODE [wrl-classic-com-component#5](../CodeSnippet/VS_Snippets_Misc/wrl-classic-com-component#5)]  
  
2.  執行 RegScript.reg，或將它加入至您的專案 **建置後事件**。 如需詳細資訊，請參閱 [建置前事件/建置後事件命令列對話方塊](../Topic/Pre-build%20Event-Post-build%20Event%20Command%20Line%20Dialog%20Box.md)。  
  
3.  新增 **Win32 主控台應用程式** 專案加入方案。 為專案命名，例如 `Calculator`。  
  
4.  使用此程式碼取代 Calculator.cpp 的內容：  
  
     [!code-cpp[wrl-classic-com-component#6](../windows/codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_6.cpp)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 這份文件使用標準 COM 函式，以示範您可以使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 撰寫 COM 元件，並使其可供任何啟用 COM 的技術使用。 您也可以使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 型別，例如 [Microsoft::WRL::ComPtr](../windows/comptr-class.md) 中傳統型應用程式管理 COM 和其他物件的存留期。 下列程式碼會使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 來管理 `ICalculatorComponent` 指標的存留期。 `CoInitializeWrapper` 類別是 RAII 包裝函式，可保證釋放 COM 程式庫，也可保證 COM 程式庫的存留期超過 `ComPtr` 智慧型指標物件的存留期。  
  
 [!code-cpp[wrl-classic-com-component#7](../windows/codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_7.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [Windows 執行階段 c + + 樣板程式庫 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)