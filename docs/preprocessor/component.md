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
ms.openlocfilehash: 578c590bdb4223f173e0249c18d0eea4e78a18db
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220473"
---
# <a name="component-pragma"></a>component pragma

控制來源檔案內的流覽資訊或相依性資訊的集合。

## <a name="syntax"></a>語法

> **#pragma 元件 (瀏覽器,** { **on**  |  **off** } [ **,** **參考**[ **,** *名稱*]] **)**  \
> **#pragma 元件 (minrebuild,** { **on**  |  **off** } **)**  \
> **#pragma 元件 (mintypeinfo,** { **on**  |  **off** } **)**

## <a name="remarks"></a>備註

### <a name="browser"></a>Browser

您可以開啟或關閉收集功能，而且可以指定要在收集的資訊中忽略的特定名稱。

使用開啟或關閉來控制收集 pragma 前方的瀏覽資訊。 例如：

```cpp
#pragma component(browser, off)
```

讓編譯器停止收集瀏覽資訊。

> [!NOTE]
> 若要使用這個 pragma 開啟流覽資訊的收集,[必須先啟用 [流覽資訊]](../build/reference/building-browse-information-files-overview.md)。

**References**選項可以搭配或不搭配*name*引數使用。 使用沒有*名稱*的**參考**會開啟或關閉參考的收集 (不過, 仍會繼續收集其他流覽資訊)。 例如：

```cpp
#pragma component(browser, off, references)
```

讓編譯器停止收集參考資訊。

使用*name*和**off**的**參考**, 可防止 [流覽資訊] 視窗中顯示*名稱*的參考。 使用這個語法會忽略您沒有興趣的名稱和類型，並可減少瀏覽資訊檔的大小。 例如：

```cpp
#pragma component(browser, off, references, DWORD)
```

從該點開始忽略 DWORD 的參考。 您可以使用**on**來開啟對 DWORD 的參考收集:

```cpp
#pragma component(browser, on, references, DWORD)
```

這是繼續收集*名稱*參考的唯一方法;您必須明確地開啟已關閉的任何*名稱*。

若要防止預處理器展開*名稱*(例如將 Null 展開為 0), 請在其前後加上引號:

```cpp
#pragma component(browser, off, references, "NULL")
```

### <a name="minimal-rebuild"></a>最少重建

已淘汰的[/gm (啟用最少重建)](../build/reference/gm-enable-minimal-rebuild.md)功能需要編譯器建立和儲存C++類別相依性資訊, 以取得磁碟空間。 若要節省磁碟空間, 您可以`#pragma component( minrebuild, off )`在不需要收集相依性資訊時使用, 例如, 在不變的標頭檔中。 在`#pragma component( minrebuild, on )`不變的類別之後插入, 以重新開啟相依性集合。

### <a name="reduce-type-information"></a>減少類型資訊

`mintypeinfo`選項會減少指定區域的偵錯工具資訊。 這項資訊的容量相當可觀，會影響到 .pdb 和 .obj 檔案。 您無法在 mintypeinfo 區域中偵錯類別和結構。 使用 mintypeinfo 選項可避免下列警告：

```cmd
LINK : warning LNK4018: too many type indexes in PDB "filename", discarding subsequent type information
```

如需詳細資訊, 請參閱[/gm (啟用最少重建)](../build/reference/gm-enable-minimal-rebuild.md)編譯器選項。

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
