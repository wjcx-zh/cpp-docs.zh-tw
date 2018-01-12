---
title: "CLR 整合 (C + + /CX) |Microsoft 文件"
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76e213cf-2f3d-4181-b35b-9fd25d5b307c
caps.latest.revision: "10"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f9851a7aa0d1dad84a37504b479c551ffa63bcf9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="clr-integration-ccx"></a>CLR 整合 (C++/CX)
某些 Windows 執行階段類型接收特殊處理，在 C + + /CX 和 common language runtime (CLR) 為基礎的語言。 這篇文章討論一種語言的數個類型如何對應到另一種語言。 例如，CLR 將 Windows.Foundation.IVector 對應到 System.Collections.IList、將 Windows.Foundation.IMap 對應到 System.Collections.IDictionary 等等。 同樣地，C + + /CX 特別對應的類型，例如 platform:: delegate 和 platform:: string。  
  
## <a name="mapping-the-windows-runtime-to-ccx"></a>將 Windows 執行階段對應至 C + + /CX  
 當 C + + /CX 讀取 Windows 中繼資料 (.winmd) 檔案，編譯器會自動對應通用的 Windows 執行階段命名空間和類型至 C + + /CX 命名空間和類型。 例如，數字的 Windows 執行階段類型`UInt32`自動對應到`default::uint32`。  
  
 C + + /CX 會將對應至數個其他 Windows 執行階段類型**平台**命名空間。 例如， **windows:: foundation** HSTRING 控制代碼，代表唯讀的 Unicode 文字字串，會對應至 C + + /CX`Platform::String`類別。 當 Windows 執行階段作業會傳回錯誤 HRESULT 時，它會對應至 C + + /CX `Platform::Exception`。 如需詳細資訊，請參閱 [Built-in Types](http://msdn.microsoft.com/en-us/acc196fd-09da-4882-b554-6c94685ec75f)。  
  
 C + + /CX 也會對應 Windows 執行階段命名空間中特定類型，以增強類型的功能。 針對這些類型，C + + /CX 提供協助程式建構函式和 c + + 特有和類型的標準.winmd 檔案中沒有可用的方法。  
  
 下列清單顯示支援新建構函式和 Helper 方法的值結構。 如果之前撰寫的程式碼使用結構初始設定清單，請變更為使用新加入的建構函式。  
  
 **Windows::Foundation**  
  
-   點  
  
-   Rect  
  
-   大小  
  
 **Windows::UI**  
  
-   色彩  
  
 **Windows::UI::Xaml**  
  
-   CornerRadius  
  
-   持續期間  
  
-   GridLength  
  
-   Thickness  
  
 **Windows::UI::Xaml::Interop**  
  
1.  TypeName  
  
 **Windows::UI::Xaml::Media**  
  
-   矩陣  
  
 **Windows::UI::Xaml::Media::Animation**  
  
-   KeyTime  
  
-   RepeatBehavior  
  
 **Windows::UI::Xaml::Media::Media3D**  
  
-   Matrix3D  
  
## <a name="mapping-the-clr-to-ccx"></a>將 CLR 對應至 C + + /CX  
 當 Visual c + + 或 C# 編譯器讀取.winmd 檔案時，自動對應中繼資料檔案中的某些類型到適當的 C + + /CX 或 CLR 類型。 例如，在 CLR IVector\<T > 介面會對應至 IList\<T >。 但在 C + + /CX、 IVector\<T > 介面未對應到另一種類型。  
  
 Ireference<t>\<T > 在 Windows 執行階段都對應到可為 Null\<T > 在.NET 中。  
  
## <a name="see-also"></a>請參閱  
 [與其他語言間的互通性](../cppcx/interoperating-with-other-languages-c-cx.md)