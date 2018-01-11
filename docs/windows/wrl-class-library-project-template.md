---
title: "WRL 類別庫專案範本 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
ms.assetid: 628b0852-89e5-44f8-bf58-a09762bda15c
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 13fc476f696bdd2cb17ed58c496c63747db90322
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="wrl-class-library-project-template"></a>WRL 類別庫專案範本
如果您使用 Visual Studio 來撰寫 Windows 執行階段 c + + 樣板程式庫 (WRL) 專案，您可大幅簡化您的工作，藉由下載 WRL 類別庫專案範本。  
  
> [!NOTE]
>  如果您必須手動更新現有的專案的專案設定，請參閱[Dll (C + + /CX)](http://msdn.microsoft.com/library/windows/apps/hh699881\(v=vs.110\).aspx)。  
  
## <a name="download-the-wrl-project-template"></a>下載 WRL 專案範本  
 Visual Studio 不提供對 Windows 執行階段 c + + 樣板程式庫專案的範本。 以下是如何下載與 Windows 執行階段 c + + 樣板程式庫建立通用 Windows 平台應用程式之基本類別庫專案範本。  
  
#### <a name="to-download-the-wrl-project-template"></a>若要下載 WRL 專案範本  
  
1.  在功能表列上選擇 **檔案**，**新專案**。  
  
2.  在左窗格中**新專案**對話方塊中，選取**線上**，然後選取**範本**。  
  
3.  在**搜尋線上範本**方塊右上角，型別中`WRL Class Library`。 當該範本會出現在搜尋結果中時，選擇**確定** 按鈕。  
  
4.  在**下載並安裝**對話方塊中，如果您同意授權條款，請選擇**安裝** 按鈕。  
  
5.  安裝範本之後，建立專案，選擇**檔案**，**新專案**，然後選取`WRLClassLibrary`範本。 專案建立 DLL。  
  
## <a name="examples-that-use-the-project-template"></a>使用專案範本的範例  
 讀取[逐步解說： 建立基本 Windows 執行階段元件](../windows/walkthrough-creating-a-basic-windows-runtime-component-using-wrl.md)的範例，會使用此範本建立 Windows 執行階段元件。  
  
## <a name="what-the-project-template-provides"></a>專案範本所提供的功能  
 專案範本提供：  
  
-   .idl 檔案宣告的基本介面的 MIDL 屬性其類別實作。 以下為範例。  
  
     [!code-cpp[wrl-project-template#1](../windows/codesnippet/CPP/wrl-class-library-project-template_1.idl)]  
  
-   定義類別實作的.cpp 檔案。 以下為範例。  
  
     [!code-cpp[wrl-project-template#2](../windows/codesnippet/CPP/wrl-class-library-project-template_2.cpp)]  
  
     [RuntimeClass](../windows/runtimeclass-class.md)幫助您管理的模組中的所有物件的全域參考基底類別，並宣告的方法[IUnknown](http://msdn.microsoft.com/en-us/33f1d79a-33fc-4ce5-a372-e08bda378332)和[IInspectable](http://msdn.microsoft.com/en-us/0657e51f-d4c0-46c6-927d-b01e54b6846c)介面。 [InspectableClass](../windows/inspectableclass-macro.md)巨集會實作`IUnknown`和`IInspectable`。 [ActivatableClass](../windows/activatableclass-macros.md)巨集建立的類別處理站所建立的類別執行個體。  
  
-   名為 module.cpp 定義程式庫匯出`DllMain`， `DllCanUnloadNow`， `DllGetActivationFactory`，和`DllGetClassObject`。  
  
## <a name="see-also"></a>請參閱  
 [Windows 執行階段 C++ 範本庫 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)