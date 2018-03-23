---
title: 如何： 多個 PGO 設定檔合併至單一設定檔 |Microsoft 文件
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- merging profiles
- profile-guided optimizations, merging profiles
ms.assetid: aab686b5-59dd-40d1-a04b-5064690f65a6
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 450aa6c763c44176ce6cb03313abcb419dc7315c
ms.sourcegitcommit: ee7d74683af7631441c8c7f65ef5ceceaee4a5ee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="how-to-merge-multiple-pgo-profiles-into-a-single-profile"></a>如何：將多個 PGO 設定檔合併至單一設定檔

特性指引最佳化 (PGO) 是用於建立最佳化的二進位檔會分析的案例為基礎的絕佳工具。 但是，如果您有幾個重要、 但不同案例的應用程式？ 如何建立單一設定檔 PGO 可以使用數個不同的案例？ 在 Visual Studio 中，PGO 管理員[pgomgr.exe](pgomgr.md)，會為您完成此作業。

合併設定檔的語法為：

`pgomgr /merge[:num] [.pgc_files] .pgd_files`

其中`num`是選擇性的加權，用於加入這項合併的.pgc 檔案。 如果是更重要的是比其他某些情況下，或要多次執行的情況下，常用於加權。

> [!NOTE]
> PGO 管理員不適用於過時的設定檔資料。 若要合併的.pgc 檔案到.pgd 檔，.pgc 檔案必須產生可執行檔所建立的相同連結引動過程，產生的.pgd 檔。

## <a name="examples"></a>範例

在此範例中，PGO 管理員會加入 pgcFile.pgc pgdFile.pgd 六次：

`pgomgr /merge:6 pgcFile.pgc pgdFile.pgd`

在此範例中，PGO 管理員會將 pgcFile1.pgc 和 pgcFile2.pgc 加入 pgdFile.pgd，兩次，每個.pgc 檔案：

`pgomgr /merge:2 pgcFile1.pgc pgcFile2.pgc pgdFile.pgd`

如果沒有任何.pgc 檔案引數執行 PGO 管理員時，它會搜尋所有具有相同基底名稱後面接著驚嘆號 （！），然後一個或多個的任意字元的.pgd 檔的.pgc 檔案的本機目錄。 例如，如果本機目錄含有檔案 test.pgd、 test!1.pgc、 test2.pgc 和 test!hello.pgc，並接著執行從本機目錄，下列命令**pgomgr**將 test!1.pgc 和 test!hello.pgc test.pgd 成。

`pgomgr /merge test.pgd`

## <a name="see-also"></a>另請參閱

[特性指引最佳化](../../build/reference/profile-guided-optimizations.md)
