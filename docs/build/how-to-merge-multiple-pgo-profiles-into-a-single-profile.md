---
title: 如何：將多個 PGO 設定檔合併至單一設定檔
ms.date: 03/14/2018
helpviewer_keywords:
- merging profiles
- profile-guided optimizations, merging profiles
ms.assetid: aab686b5-59dd-40d1-a04b-5064690f65a6
ms.openlocfilehash: 451c0f30a271f5dce3974e172766da4a23340b93
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188869"
---
# <a name="how-to-merge-multiple-pgo-profiles-into-a-single-profile"></a>如何：將多個 PGO 設定檔合併至單一設定檔

特性指引優化（PGO）是一個絕佳的工具，可根據所分析的案例建立優化的二進位檔。 但如果您的應用程式有數個重要但不同的案例，該怎麼辦？ 您要如何建立 PGO 可以從數個不同案例使用的單一設定檔？ 在 Visual Studio 中，PGO 管理員[pgomgr](pgomgr.md)會為您執行這項工作。

合併設定檔的語法如下：

`pgomgr /merge[:num] [.pgc_files] .pgd_files`

其中`num`是要用於此合併所新增之 .pgc 檔案的選擇性權數。 如果有某些案例比其他情況更重要，或有多個案例要執行多次，通常會使用權數。

> [!NOTE]
> PGO 管理員無法處理過時的設定檔資料。 若要將 .pgc 檔合併成 .pgd 檔案，必須由產生 .pgd 檔案的相同連結調用所建立的可執行檔來產生 .pgc 檔案。

## <a name="examples"></a>範例

在此範例中，PGO 管理員會將 pgcFile 新增至 pgdFile 的六次：

`pgomgr /merge:6 pgcFile.pgc pgdFile.pgd`

在此範例中，PGO 管理員會將 pgcFile1 和 pgcFile2 新增至 pgdFile，每個 .pgc 檔案兩次：

`pgomgr /merge:2 pgcFile1.pgc pgcFile2.pgc pgdFile.pgd`

如果執行 PGO 管理員時沒有任何 .pgc 檔案引數，它會在本機目錄中搜尋所有副檔名為 .pgd 檔案相同的 .pgc 檔案，後面接著驚嘆號（！），然後是一或多個任一字元。 例如，如果本機目錄有檔案 test .pgd，test！ 1 .pgc，test2 .pgc，和 test！ hello. .pgc，而下列命令則是從本機目錄執行，然後**pgomgr**將 test！ 1 .pgc 和 test！ hello .pgc 合併到 test. .pgd。

`pgomgr /merge test.pgd`

## <a name="see-also"></a>請參閱

[特性指引最佳化](profile-guided-optimizations.md)
