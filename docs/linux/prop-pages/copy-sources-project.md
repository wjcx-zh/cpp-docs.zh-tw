---
title: 複製來源專案屬性 (Linux C++)
ms.date: 10/16/2019
ms.assetid: 1a44230d-5dd8-4d33-93b4-e77e03e00150
ms.openlocfilehash: 732a13520a223f1aa73733cd4098c247052f8d3b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "79441382"
---
# <a name="copy-sources-project-properties-linux-c"></a>複製來源專案屬性 (Linux C++)

::: moniker range="vs-2015"

Visual Studio 2017 及更新版本支援 Linux。

::: moniker-end

::: moniker range=">=vs-2017"

此屬性頁面上設定的屬性，會套用至專案中的所有檔案，但已設定檔案層級屬性的專案除外。

| 屬性 | 描述 |
|--|--|
| 要複製的來源 | 指定要複製到遠端系統的來源。 變更此清單可能會造成遠端系統上作為檔案複製目標的目錄結構變更，或到受影響。 |
| 複製來源 | 指定是否要將來源複製到遠端系統。 |
| 要複製的其他來源 | 指定要複製到遠端系統的其他來源。 選擇使用這樣的語法指定本地到遠端映射對:完全本地路徑1:=完全遠端路徑1;完全本地路徑2:=完全遠端路徑2,其中本地檔案可以複製到遠端系統上的指定遠端位置。 |

@SourcesToCopyRemotely並@DataFilesToCopyRemotely參考專案檔中的項目群組。 要修改遠端複製的來源或資料檔,請編輯*vcxproj*檔,如下所示:

```xml
<ItemGroup>
   <MyItems Include="foo.txt" />
   <MyItems Include="bar.txt" />
   <DataFilesToCopyRemotely Include="@(MyItems)" />
</ItemGroup>
```

::: moniker-end
