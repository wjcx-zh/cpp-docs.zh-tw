---
title: 複製來源專案屬性 (Linux C++)
ms.date: 10/16/2019
ms.assetid: 1a44230d-5dd8-4d33-93b4-e77e03e00150
ms.openlocfilehash: ceaa1240f08b83ebc83bd7fdc25a3215467eb3f1
ms.sourcegitcommit: 9aab425662a66825772f091112986952f341f7c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444951"
---
# <a name="copy-sources-project-properties-linux-c"></a>複製來源專案屬性 (Linux C++)

::: moniker range="vs-2015"

Visual Studio 2017 及更新版本支援 Linux。

::: moniker-end

::: moniker range=">=vs-2017"

此屬性頁面上設定的屬性，會套用至專案中的所有檔案，但已設定檔案層級屬性的專案除外。

屬性 | 描述
--- | ---
要複製的來源 | 指定要複製到遠端系統的來源。 變更此清單可能會造成遠端系統上作為檔案複製目標的目錄結構變更，或到受影響。
複製來源 | 指定是否要將來源複製到遠端系統。
要複製的其他來源 | 指定要複製到遠端系統的其他來源。 您也可以使用類似如下的語法，將清單提供為本機到遠端的對應配對：fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2，如此會將本機檔案複製到遠端系統上指定的遠端位置。

@SourcesToCopyRemotely 和 @DataFilesToCopyRemotely 指的是專案檔中的專案群組。 若要修改遠端複製哪些來源或資料檔案，請編輯 *.vcxproj*檔案，如下所示：

```xml
<ItemGroup>
   <MyItems Include=“foo.txt” />
   <MyItems Include=“bar.txt” />
   <DataFilesToCopyRemotely Include=”@(MyItems)” />
</ItemGroup>
```

::: moniker-end
