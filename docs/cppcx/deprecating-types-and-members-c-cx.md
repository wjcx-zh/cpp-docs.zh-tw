---
title: "將類型和成員設為已被取代 (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b20b01c1-a439-4ff0-8cf3-d7280c492813
caps.latest.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 7
---
# 將類型和成員設為已被取代 (C++/CX)
在 C\+\+\/CX，支援使用 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 屬性，將生產者和消費者的 [Deprecated](http://msdn.microsoft.com/zh-tw/8b02ad36-3b5f-4361-888b-e6a99040e57c)類型和成員設為已被取代。 如果您使用的 API 已套用這個屬性，您會收到一個編譯時期警告訊息，表示 API 已被取代，此外建議替代的 API 以供使用。 在您的公用類型和方法，可以套用這個屬性並提供自訂訊息。  
  
> [!CAUTION]
>  [Deprecated](http://msdn.microsoft.com/zh-tw/8b02ad36-3b5f-4361-888b-e6a99040e57c) 屬性只能搭配 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]類型一起使用。 如果是 Standard C\+\+ 類別和成員，請使用 [\_\_declspec\(deprecated\)](http://msdn.microsoft.com/library/044swk7y.aspx)。  
  
## 範例  
 下列範例示範如何 \(例如在 Windows 執行階段元件中\) 將您的公用 API 設為已被取代。 第二個參數，其類型為 [Windows:Foundation::Metadata::DeprecationType](http://msdn.microsoft.com/zh-tw/ee01e63d-37d0-4273-accc-fca174f88bfa)，指定 API 正要被取代或移除。 目前只支援 DeprecationType::Deprecated 值。 屬性中的第三個參數指定要套用屬性的 [Windows::Foundation::Metadata::Platform](http://msdn.microsoft.com/zh-tw/1eae292d-1ab7-4d97-a58c-b0beffd51ef5)。  
  
```  
  
namespace wfm = Windows::Foundation::Metadata; public ref class Bicycle sealed { public: property double Speed; [wfm::Deprecated("Use the Speed property to compute the angular speed of the wheel", wfm::DeprecationType::Deprecate, 0x0)] double ComputeAngularVelocity(); };  
```  
  
## 支援的目標  
 下表列出可套用 Deprecated 屬性的建構：  
  
||  
|-|  
|XAML 控制項|  
|Delegate \- 委派|  
|Event \- 事件|  
|列舉欄位|  
|enum|  
|struct|  
|方法|  
|Class \- 類別|  
|interface|  
|屬性|  
|結構欄位|  
|參數化建構函式|  
  
## 請參閱  
 [類型系統](../cppcx/type-system-c-cx.md)   
 [Visual C\+\+ 語言參考](../cppcx/visual-c-language-reference-c-cx.md)   
 [命名空間參考](../cppcx/namespaces-reference-c-cx.md)