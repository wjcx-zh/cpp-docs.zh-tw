---
title: HOW TO：合併在單一設定檔中的多個 PGO 設定檔
ms.date: 03/14/2018
helpviewer_keywords:
- merging profiles
- profile-guided optimizations, merging profiles
ms.assetid: aab686b5-59dd-40d1-a04b-5064690f65a6
ms.openlocfilehash: 451c0f30a271f5dce3974e172766da4a23340b93
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57824883"
---
# <a name="how-to-merge-multiple-pgo-profiles-into-a-single-profile"></a>HOW TO：合併在單一設定檔中的多個 PGO 設定檔

特性指引最佳化 (PGO) 是不錯的工具來建立分析的案例為基礎的最佳化二進位檔。 但是如果您有具有數個重要、 尚未相異案例的應用程式？ 如何建立單一設定檔，可以使用 PGO 從數個不同的案例？ 在 Visual Studio 中，PGO 管理員 中， [pgomgr.exe](pgomgr.md)，會為您完成此作業。

合併設定檔的語法是：

`pgomgr /merge[:num] [.pgc_files] .pgd_files`

其中`num`是選擇性的權數，將用於新增這項合併的.pgc 檔案。 如果有一些會比其他人更重要的案例，或者是在執行多次的情況下通常用於權數。

> [!NOTE]
> PGO 管理員不適用於過時的設定檔資料。 若要合併的.pgc 檔案至.pgd 檔案，.pgc 檔案必須產生可執行檔建立的相同連結引動過程所產生的.pgd 檔案。

## <a name="examples"></a>範例

在此範例中，PGO 管理員將 pgcFile.pgc pgdFile.pgd 六次：

`pgomgr /merge:6 pgcFile.pgc pgdFile.pgd`

在此範例中，PGO 管理員會將 pgcFile1.pgc 和 pgcFile2.pgc 加入 pgdFile.pgd，兩次，每個.pgc 檔案：

`pgomgr /merge:2 pgcFile1.pgc pgcFile2.pgc pgdFile.pgd`

如果不含任何的.pgc 檔案引數執行 PGO 管理員時，它會搜尋所有的.pgc 檔案具有相同的基底名稱後面加上驚嘆號 （！） 和接著一或多個的任意字元的.pgd 檔的本機目錄。 例如，如果本機目錄含有檔案 test.pgd、 test!1.pgc、 test2.pgc 和 test!hello.pgc，並執行下列命令會從本機目錄中，然後**pgomgr**將 test!1.pgc 和 test!hello.pgc 成 test.pgd。

`pgomgr /merge test.pgd`

## <a name="see-also"></a>另請參閱

[特性指引最佳化](profile-guided-optimizations.md)
