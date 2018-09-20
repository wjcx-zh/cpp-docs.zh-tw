---
title: 覆寫 （c + + 元件延伸模組） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- overriding, override keyword [C++]
- override keyword [C++]
ms.assetid: 34d19257-1686-4fcd-96f5-af07c70ba914
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6071cef3d5669fda86975bb0f27a2b9b87eeb011
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46407266"
---
# <a name="override--c-component-extensions"></a>override (C++ 元件擴充功能)

**覆寫**即時線上關鍵字表示類型的成員，可以覆寫基底類別或基底介面成員。

## <a name="remarks"></a>備註

**覆寫**關鍵字對原生目標 （預設編譯器選項），在編譯時是有效 Windows 執行階段目標 (`/ZW`編譯器選項)，或通用語言執行階段目標 (`/clr`編譯器選項)。

如需有關覆寫指定名稱的詳細資訊，請參閱[覆寫規範](../cpp/override-specifier.md)並[覆寫規範和原生編譯](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)。

如需有關內容相關性關鍵字的詳細資訊，請參閱[即時線上關鍵字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。

## <a name="examples"></a>範例

下列程式碼範例顯示**覆寫**也可用在原生編譯中。

```cpp
// override_keyword_1.cpp
// compile with: /c
struct I1 {
   virtual void f();
};

struct X : public I1 {
   virtual void f() override {}
};
```

### <a name="example"></a>範例

下列程式碼範例顯示**覆寫**可用在 Windows 執行階段編譯。

```cpp 
// override_keyword_2.cpp
// compile with: /ZW /c
ref struct I1 {
   virtual void f();
};

ref struct X : public I1 {
   virtual void f() override {}
};
```

#### <a name="requirements"></a>需求

編譯器選項：`/ZW`

### <a name="example"></a>範例

下列程式碼範例顯示**覆寫**可用在通用語言執行階段編譯。

```cpp
// override_keyword_3.cpp
// compile with: /clr /c
ref struct I1 {
   virtual void f();
};

ref struct X : public I1 {
   virtual void f() override {}
};
```

#### <a name="requirements"></a>需求

編譯器選項：`/clr`

## <a name="see-also"></a>另請參閱

[override 規範](../cpp/override-specifier.md)<br/>
[覆寫規範](../windows/override-specifiers-cpp-component-extensions.md)