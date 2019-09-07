---
title: CLR 整合 (C++/CX)
ms.date: 01/22/2017
ms.assetid: 76e213cf-2f3d-4181-b35b-9fd25d5b307c
ms.openlocfilehash: 44ef35d1a62706cae37285c06547a8b9b7deb35c
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740286"
---
# <a name="clr-integration-ccx"></a>CLR 整合 (C++/CX)

某些 Windows 執行階段類型會接收/Cx 中C++的特殊處理，以及以 common language RUNTIME （CLR）為基礎的語言。 這篇文章討論一種語言的數個類型如何對應到另一種語言。 例如，CLR 將 Windows.Foundation.IVector 對應到 System.Collections.IList、將 Windows.Foundation.IMap 對應到 System.Collections.IDictionary 等等。 同樣地C++，/cx 特別對應的類型，例如 platform：:D 委派和 platform：： String。

## <a name="mapping-the-windows-runtime-to-ccx"></a>將 Windows 執行階段對應到C++/cx

當C++/Cx 讀取 Windows 中繼資料（winmd）檔案時，編譯器會自動將常見的 Windows 執行階段命名空間和C++類型對應到/cx 命名空間和類型。 例如，數值 Windows 執行階段類型`UInt32`會自動對應至。 `default::uint32`

C++/CX 會將數個其他 Windows 執行階段類型對應至**Platform**命名空間。 例如，代表唯讀 Unicode 文字字串的**Windows：： Foundation** HSTRING 控制碼會對應到C++/cx `Platform::String`類別。 當 Windows 執行階段作業傳回錯誤 HRESULT 時，它會對應至C++/cx。 `Platform::Exception`

C++/Cx 也會對應 Windows 執行階段命名空間中的某些類型，以加強型別的功能。 針對這些類型， C++/cx 提供的 helper 函式和方法是特定C++的，而且無法在類型的標準 winmd 檔案中使用。

下列清單顯示支援新建構函式和 Helper 方法的值結構。 如果之前撰寫的程式碼使用結構初始設定清單，請變更為使用新加入的建構函式。

**Windows::Foundation**

- 點

- Rect

- 大小

**Windows::UI**

- 色彩

**Windows::UI::Xaml**

- CornerRadius

- Duration

- GridLength

- Thickness

**Windows::UI::Xaml::Interop**

- TypeName

**Windows::UI::Xaml::Media**

- 矩陣

**Windows::UI::Xaml::Media::Animation**

- KeyTime

- RepeatBehavior

**Windows::UI::Xaml::Media::Media3D**

- Matrix3D

## <a name="mapping-the-clr-to-ccx"></a>將 CLR 對應到C++/cx

當 Microsoft C++或C#編譯器讀取 winmd 檔案時，會自動將中繼資料檔案中的特定類型對應至適當C++的/cx 或 CLR 類型。 例如，在 CLR 中，IVector\<T > 介面會對應到 IList\<t >。 但是在C++/cx 中，IVector\<T > 介面並未對應到另一個類型。

Windows 執行階段\<中的 IReference t > 對應到 .net\<中可為 null 的 t >。

## <a name="see-also"></a>另請參閱

[與其他語言交互操作](../cppcx/interoperating-with-other-languages-c-cx.md)
