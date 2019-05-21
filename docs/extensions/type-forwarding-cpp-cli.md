---
title: 類型轉送 (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- type forwarding, C++
ms.assetid: ae730b69-0c27-41cc-84e1-3132783866ea
ms.openlocfilehash: c5148c05e5580942d885b310e35f3b629224a654
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515973"
---
# <a name="type-forwarding-ccli"></a>類型轉送 (C++/CLI)

*類型轉送*可讓您將類型從某個組件 (組件 A) 移到另一個組件 (組件 B) 中，因此就不需要重新編譯使用組件 A 的用戶端。

## <a name="windows-runtime"></a>Windows 執行階段

Windows 執行階段不支援此功能。

## <a name="common-language-runtime"></a>Common Language Runtime

下列程式碼範例會示範如何使用類型轉送。

### <a name="syntax"></a>語法

```cpp
#using "new.dll"
[assembly:TypeForwardedTo(type::typeid)];
```

### <a name="parameters"></a>參數

*new*<br/>
類型定義移動之後所在的組件。

*type*<br/>
要移動至另一個組件之定義的類型。

### <a name="remarks"></a>備註

在寄送元件 (組件) 並由用戶端應用程式使用之後，您可以使用類型轉送將類型從該元件 (組件) 移到另一個組件，接著寄送已更新的元件 (和任何其他必要組件)，用戶端應用程式就能在不需要重新編譯的情況下仍正常運作。

類型轉送僅適用於現有應用程式所參考的元件。 當您重建應用程式時，應用程式中所使用的任何類型都必須有適當的組件參考。

從組件轉送類型 (類型 A) 時，必須為該類型新增 `TypeForwardedTo` 屬性，以及組件參考。 您參考的組件必須包含下列其中一個：

- 類型 A 的定義。

- 類型 A 的 `TypeForwardedTo` 屬性，以及組件參考。

可轉送類型的範例包括：

- ref 類別

- 實值類別

- 列舉

- 介面

您無法轉送下列類型：

- 泛型類型

- 原生類型

- 巢狀類型 (如果想要轉送巢狀類型，則應轉送封入類型)

您可以將類型轉送至任何以 Common Language Runtime 為目標的語言所撰寫的組件。

因此，如果用來建置組件 A.dll 的原始程式碼檔案包含類型定義 (`ref class MyClass`)，且您想要將該類型定義移至組件 B.dll，您可以：

1. 將 `MyClass` 類型定義移至用來建置 B.dll 的原始程式碼檔案。

2. 建置組件 B.dll

3. 將 `MyClass` 類型定義從用來建置 A.dll 的原始程式碼中刪除，並將它取代為以下定義：

    ```cpp
    #using "B.dll"
    [assembly:TypeForwardedTo(MyClass::typeid)];
    ```

4. 建置組件 A.dll。

5. 在不需要重新編譯用戶端應用程式的情況下使用 A.dll。

### <a name="requirements"></a>需求

編譯器選項：`/clr`