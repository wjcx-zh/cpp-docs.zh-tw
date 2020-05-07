---
title: pgomgr
ms.date: 03/14/2018
helpviewer_keywords:
- pgomgr program
- profile-guided optimizations, pgomgr
ms.assetid: 74589126-df18-42c9-8739-26d60e148d6a
ms.openlocfilehash: 4e3eb08c88db9d0ed4e47649014a600c3e0ccb78
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295235"
---
# <a name="pgomgr"></a>pgomgr

將一個或多個 .pgc 檔案中的設定檔資料新增至 .pgd 檔案。

## <a name="syntax"></a>語法

> **pgomgr** [*options*] *pgcfiles* *pgdfile*

### <a name="parameters"></a>參數

*options*<br/>
您可以指定下列選項來**pgomgr**：

- **/help** 或 **/?** 顯示可用的**pgomgr**選項。

- **/clear**會清除所有設定檔資訊的 .pgd 檔案。 當您指定 **/clear**時，無法指定 .pgc 檔。

- **/detail**顯示詳細的統計資料，包括流程圖涵蓋範圍資訊。

- **/summary**顯示每個函數的統計資料。

- **/unique**與 **/summary**搭配使用時，會造成裝飾函數名稱顯示。 當未使用 **/unique**時，預設值為要顯示的未修飾函式名稱。

- **/merge**\[**：**<em>n</em>] 會導致 .pgc 檔案或檔案中的資料加入至 .pgd 檔案。 選擇性參數*n*可讓您指定應將資料加入*n*次。 例如，如果案例通常會完成六次，以反映客戶完成的頻率，您可以在測試回合中執行一次，並使用**pgomgr/merge： 6**將它加入至 .pgd 檔案六次。

*pgcfiles*<br/>
一或多個要合併到 .pgd 檔案中的設定檔資料的 .pgc 檔。 您可以指定單一 .pgc 檔案或多個 .pgc 檔案。 如果您未指定任何 .pgc 檔， **pgomgr**會合並其檔案名與 .pgd 檔案相同的所有 .pgc 檔案。

*pgdfile*<br/>
您要將 .pgc 檔案中的資料合併到其中的 .pgd 檔案。

## <a name="remarks"></a>備註

> [!NOTE]
> 您只能從 Visual Studio 的開發人員命令提示字元啟動此工具。 您無法從系統命令提示字元，或從 [檔案總管] 啟動它。

## <a name="example"></a>範例

此範例命令會清除設定檔資料的 myapp .pgd 檔案：

`pgomgr /clear myapp.pgd`

此範例命令會將 myapp1 中的設定檔資料新增至 .pgd 檔案三次：

`pgomgr /merge:3 myapp1.pgc myapp.pgd`

在此範例中，會將所有 myapp # .pgc 檔案中的資料，新增至 myapp .pgd 檔。

`pgomgr -merge myapp1.pgd`

## <a name="see-also"></a>請參閱

[特性指引最佳化](profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>
[pgosweep](pgosweep.md)<br/>
