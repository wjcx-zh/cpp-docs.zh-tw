---
title: /HEAP
description: MSVC 連結器或 EDITBIN/HEAP 選項會設定堆積大小的總計，以及選擇性的其他堆積區塊大小。
ms.date: 07/07/2020
f1_keywords:
- /heap
helpviewer_keywords:
- heap allocation, setting heap size
- HEAP editbin option
- -HEAP editbin option
- /HEAP editbin option
ms.assetid: 6ce759b5-75b7-44ff-a5fd-3a83a0ba9a48
ms.openlocfilehash: 7976ae2927ca731c83fa42e87da182fee4df3d7c
ms.sourcegitcommit: e17cc8a478b51739d67304d7d82422967b35f716
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/08/2020
ms.locfileid: "86127829"
---
# `/HEAP`

設定堆積的大小 (位元組)。 這個選項只適用於可執行檔。

## <a name="syntax"></a>語法

> **`/HEAP:`**_`reserve`_\[**`,`**_`commit`_]

## <a name="remarks"></a>備註

*`reserve`* 引數會指定虛擬記憶體中初始堆積配置的總數。 **`/HEAP`** 連結器或[EDITBIN](editbin-reference.md)選項會將指定的值舍入至最接近4個位元組的倍數。 預設的堆積大小為 1 MB。

選擇性 *`commit`* 引數受限於作業系統的轉譯。 在 Windows 作業系統上，它會指定要配置的初始實體記憶體數量。 它也會指定在擴展堆積時，要配置多少記憶體。 已認可的虛擬記憶體會導致在分頁檔中保留空間。 較高的 *`commit`* 值可讓系統在應用程式需要更多堆積空間時，不常配置記憶體，但會增加記憶體需求，以及可能的應用程式啟動持續時間。 此 *`commit`* 值必須小於或等於 *`reserve`* 值。 預設值為 4 KB。

*`reserve`* *`commit`* 以 Decimal、C-language 十六進位或八進位標記法指定和值。 例如，1 MB 的值以十進位表示為 1048576，以十六位元表示為 0x100000，以八進位表示為 04000000。 預設值相當於選項 **`/HEAP:1048576,4096`** 。

### <a name="example"></a>範例

此範例連結命令會建立一個可執行檔*main.exe* ，其中堆積保留為 2 MB。 初始堆積和更新版本堆積擴充會出現在 64 KB 的區塊中：

**`link /heap:0x200000,0x10000 main.obj`**

### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中設定這個連結器選項

1. 開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**  >  **連結器**  >  **系統**] 屬性頁。

1. 設定 [**堆積保留大小**] 和 [**堆積認可大小**] 屬性，然後選擇 **[確定]** **或 [** 套用] 以儲存變更。

## <a name="see-also"></a>另請參閱

[EDITBIN 選項](editbin-options.md)\
[MSVC 連結器選項](linker-options.md)
