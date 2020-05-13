---
title: 遠端封存屬性 (C++ Linux)
ms.date: 06/07/2019
ms.assetid: 5ee1e44c-8337-4c3a-b2f3-35e4be954f9f
f1_keywords: []
ms.openlocfilehash: 3b6f71d9cceccf0b0221be46bacb1294d84533cd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364294"
---
# <a name="remote-archive-properties-c-linux"></a>遠端封存屬性 (C++ Linux)

::: moniker range="vs-2015"

Visual Studio 2017 及更新版本支援 Linux。

::: moniker-end

::: moniker range=">=vs-2017"

| 屬性 | 描述 |
|--|--|
| 建立封存索引 | 建立封存索引 (由 ranlib 完成)。 此選項可加速連結作業，並降低其本身程式庫內出現的相依性。 |
| 建立精簡型封存 | 建立精簡型封存。  精簡型封存包含物件的相對路徑，而不會內嵌物件。  必須刪除現有程式庫，才可於精簡型和一般型之間切換。 |
| 建立時不發出警告 | 不要在建立程式庫時發出警告。 |
| 截斷時間戳記 | 在時間戳記與 UID/GID 使用零。 |
| 隱藏啟動橫幅 | 不要顯示版本號碼。 |
| 「詳細資訊」 | 「詳細資訊」 |
| 其他選項 | 其他選項。 |
| 輸出檔案 | /OUT 選項會覆寫 lib 所建立的程式之預設名稱與位置。 |
| 封存工具 | 指定在連結靜態物件期間要叫用的程式，或遠端系統上封存工具的路徑。 |
| 封存工具逾時 | 遠端封存工具逾時 (毫秒)。 |
| 複製輸出 | 指定是否要從遠端系統，將組建輸出檔案複製到本機電腦。 |

::: moniker-end
