---
title: CLR 整合 (C++/CX)
ms.date: 01/22/2017
ms.assetid: 76e213cf-2f3d-4181-b35b-9fd25d5b307c
ms.openlocfilehash: 7b14d8067625719b337e2c830b739269ef96dccd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461811"
---
# <a name="clr-integration-ccx"></a>CLR 整合 (C++/CX)

某些 Windows 執行階段類型接收特殊處理，在 C + + /CX 和 common language runtime (CLR) 為基礎的語言。 這篇文章討論一種語言的數個類型如何對應到另一種語言。 例如，CLR 將 Windows.Foundation.IVector 對應到 System.Collections.IList、將 Windows.Foundation.IMap 對應到 System.Collections.IDictionary 等等。 同樣地，C + + /CX 特別對應的 platform:: delegate 和 platform:: string 等型別。

## <a name="mapping-the-windows-runtime-to-ccx"></a>將 Windows 執行階段對應至 C + + /CX

當 C + + /CX 會讀取 Windows 中繼資料 (.winmd) 檔案，編譯器會自動對應，常見的 Windows 執行階段命名空間和類型 C + /CX 命名空間和類型。 例如，數字的 Windows 執行階段型別`UInt32`會自動對應到`default::uint32`。

C + + /CX 對應至數個其他 Windows 執行階段類型**平台**命名空間。 例如， **windows:: foundation** HSTRING 控制代碼，表示唯讀的 Unicode 文字字串，會對應至 C + + /CX`Platform::String`類別。 當 Windows 執行階段的作業會傳回錯誤 HRESULT 時，它會對應至 C + + /CX `Platform::Exception`。

C + + /CX 也會將對應 Windows 執行階段命名空間中特定類型，以增強類型的功能。 針對這些類型，C + + /CX 提供協助程式建構函式和 c + + 特有和類型的標準.winmd 檔案中沒有可用的方法。

下列清單顯示支援新建構函式和 Helper 方法的值結構。 如果之前撰寫的程式碼使用結構初始設定清單，請變更為使用新加入的建構函式。

**Windows::Foundation**

- 點

- Rect

- 大小

**Windows::UI**

- 色彩

**Windows::UI::Xaml**

- CornerRadius

- 持續期間

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

## <a name="mapping-the-clr-to-ccx"></a>將 CLR 對應至 C + + /CX

它們時 Visual c + + 或 C# 編譯器讀取.winmd 檔案時，會自動有對應的中繼資料檔案中的某些類型到適當的 C + + /CX 或 CLR 類型。 例如，在 CLR 中，IVector\<T > 介面會對應至 IList\<T >。 但在 C + + /CX、 IVector\<T > 介面不會對應到另一個類型。

IReference\<T > 在 Windows 執行階段會對應至 Nullable\<T > 在.NET 中。

## <a name="see-also"></a>另請參閱

[與其他語言交互操作](../cppcx/interoperating-with-other-languages-c-cx.md)