---
title: "WRL 類別庫專案範本 | Microsoft Docs"
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
ms.assetid: 628b0852-89e5-44f8-bf58-a09762bda15c
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# WRL 類別庫專案範本
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果您使用 Visual Studio 撰寫 [!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)] \([!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]\) 專案，您可以下載 WRL 類別庫專案範本，大幅簡化您的工作。  
  
> [!NOTE]
>  如果您必須手動更新現有專案的專案設定，請參閱 [DLL \(C\+\+\/CX\)](http://msdn.microsoft.com/library/windows/apps/hh699881\(v=vs.110\).aspx)。  
  
## 下載 WRL 專案範本  
 Visual Studio 不提供 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 專案的範本。  此如何下載建立 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 應用程式的基本類別庫與 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]的專案範本。  
  
#### 下載 WRL 專案範本  
  
1.  在功能表列上，選擇 \[**檔案**\]、\[**新增專案**\]。  
  
2.  在 \[**新增專案**\] 對話方塊的左窗格中，選取的 \[**上線**\]，然後選取 \[**樣板**\]。  
  
3.  在右上角的 \[**搜尋線上範本**\]方塊中，輸入 `WRL 類別庫`。  當範本會出現在搜尋結果時，請選取 \[**確定**\] 按鈕。  
  
4.  在 \[**下載及安裝**\] 對話方塊;因此，如果您同意授權條款，請選取 \[**安裝**\] 按鈕。  
  
5.  安裝在範本上後，請選取 \[**檔案**\]， \[**新增專案**\]，然後選取 建立專案 `WRLClassLibrary` 範本。  專案建立 DLL。  
  
## 使用專案範本的範例  
 讀取使用此範本來建立 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 元件的範例 [逐步解說：建立基本 Windows 執行階段元件](../windows/walkthrough-creating-a-basic-windows-runtime-component-using-wrl.md) 。  
  
## 專案範本提供哪些  
 測試專案範本提供:  
  
-   宣告 MIDL 的 .idl 檔為基礎介面歸屬其類別實作。  以下為範例。  
  
     [!code-cpp[wrl-project-template#1](../windows/codesnippet/CPP/wrl-class-library-project-template_1.idl)]  
  
-   定義類別實作的 .cpp 檔案。  以下為範例。  
  
     [!code-cpp[wrl-project-template#2](../windows/codesnippet/CPP/wrl-class-library-project-template_2.cpp)]  
  
     [RuntimeClass](../windows/runtimeclass-class.md) 基底類別來協助管理所有全域物件參考模組和宣告 [IUnknown](http://msdn.microsoft.com/zh-tw/33f1d79a-33fc-4ce5-a372-e08bda378332) 和 [IInspectable](http://msdn.microsoft.com/zh-tw/0657e51f-d4c0-46c6-927d-b01e54b6846c) 介面的方法。  [InspectableClass](../windows/inspectableclass-macro.md) 巨集實作 `IUnknown` 和 `IInspectable`。  建立類別的執行個體的 [ActivatableClass](../windows/activatableclass-macros.md) 巨集建立 Class Factory。  
  
-   檔案名稱為定義程式庫匯出 `DllMain`、 `DllCanUnloadNow`、 `DllGetActivationFactory`和 `DllGetClassObject`的 module.cpp。  
  
## 請參閱  
 [Windows Runtime C\+\+ Template Library \(WRL\)](../windows/windows-runtime-cpp-template-library-wrl.md)