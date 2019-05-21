---
title: override  (C++/CLI 和 C++/CX)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- overriding, override keyword [C++]
- override keyword [C++]
ms.assetid: 34d19257-1686-4fcd-96f5-af07c70ba914
ms.openlocfilehash: 8dc7a0a0e6cf759d956fd701d033bd773e572af3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515653"
---
# <a name="override--ccli-and-ccx"></a>override  (C++/CLI 和 C++/CX)

**override** 即時線上關鍵字表示類型成員會覆寫基底類別或基底介面成員。

## <a name="remarks"></a>備註

針對原生目標 (預設編譯器選項)、Windows 執行階段目標 (`/ZW` 編譯器選項)，或 Common Language Runtime 目標 (`/clr` 編譯器選項) 進行編譯時，**override** 關鍵字是有效的。

如需覆寫規範的詳細資訊，請參閱[覆寫規範](../cpp/override-specifier.md)與[覆寫規範和原生編譯](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)。

如需內容相關性關鍵字的詳細資訊，請參閱[即時線上關鍵字](context-sensitive-keywords-cpp-component-extensions.md)。

## <a name="examples"></a>範例

以下程式碼範例說明 **override** 也可以在原生編譯中使用。

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

以下程式碼範例說明 **override** 可以在 Windows 執行階段編譯中使用。

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

以下程式碼範例說明 **override** 可以在 Common Language Runtime 編譯中使用。

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
[覆寫指定名稱](override-specifiers-cpp-component-extensions.md)