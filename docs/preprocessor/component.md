---
title: component pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.component
- component_CPP
helpviewer_keywords:
- component pragma
- pragmas, component
ms.assetid: 7b66355e-3201-4c14-8190-f4a2a81a604a
ms.openlocfilehash: 73b308fdc426be9b403b808d4e638b4f5c1e9149
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040726"
---
# <a name="component-pragma"></a>component pragma

從原始程式檔中控制流覽資訊或相依性資訊的集合。

## <a name="syntax"></a>語法

> **#pragma 元件 ( 瀏覽器、** { **on** \| **off** } \[ **、** **參考** \[ **、** *名稱* ]] **) ** \
> **#pragma 元件 ( minrebuild，** { **on** \| **off** } **) ** \
> **#pragma 元件 ( mintypeinfo，** { **on** \| **off** } **) **

## <a name="remarks"></a>備註

### <a name="browser"></a>瀏覽器

您可以開啟或關閉收集功能，而且可以指定要在收集的資訊中忽略的特定名稱。

使用開啟或關閉來控制收集 pragma 前方的瀏覽資訊。 例如：

```cpp
#pragma component(browser, off)
```

讓編譯器停止收集瀏覽資訊。

> [!NOTE]
> 若要使用此 pragma 開啟流覽資訊的收集功能， [必須先啟用流覽資訊](../build/reference/building-browse-information-files-overview.md)。

**References**選項可以搭配或不搭配*name*引數使用。 使用不含*name*的**references**會開啟或關閉參考的收集 (其他流覽資訊仍會繼續收集，不過) 。 例如：

```cpp
#pragma component(browser, off, references)
```

讓編譯器停止收集參考資訊。

使用*name*和**off**的**參考**可防止*名稱*的參考出現在 [流覽資訊] 視窗中。 使用這個語法會忽略您沒有興趣的名稱和類型，並可減少瀏覽資訊檔的大小。 例如：

```cpp
#pragma component(browser, off, references, DWORD)
```

略過從該點開始對 DWORD 的參考。 您可以使用 **on**來開啟 DWORD 的參考重新收集：

```cpp
#pragma component(browser, on, references, DWORD)
```

這是繼續收集 *名稱*參考的唯一方法;您必須明確地開啟已關閉的任何 *名稱* 。

若要避免預處理器展開 *名稱* (例如將 Null 展開為 0) ，請在其前後加上引號：

```cpp
#pragma component(browser, off, references, "NULL")
```

### <a name="minimal-rebuild"></a>基本重建

已淘汰的 [/gm (啟用最基本的重建) ](../build/reference/gm-enable-minimal-rebuild.md) 功能需要編譯器建立和儲存 c + + 類別相依性資訊，這會佔用磁碟空間。 若要節省磁碟空間，您可以 `#pragma component( minrebuild, off )` 在不需要收集相依性資訊時使用，例如，在不變的標頭檔中。 在不 `#pragma component( minrebuild, on )` 變的類別之後插入，以重新開啟相依性集合。

### <a name="reduce-type-information"></a>減少類型資訊

`mintypeinfo`選項會減少指定區域的偵錯工具資訊。 這項資訊的容量相當可觀，會影響到 .pdb 和 .obj 檔案。 您無法在 mintypeinfo 區域中偵錯類別和結構。 使用 mintypeinfo 選項可避免下列警告：

```cmd
LINK : warning LNK4018: too many type indexes in PDB "filename", discarding subsequent type information
```

如需詳細資訊，請參閱 [/gm (啟用最基本的重建) ](../build/reference/gm-enable-minimal-rebuild.md)  編譯器選項。

## <a name="see-also"></a>另請參閱

[Pragma 指示詞與 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
