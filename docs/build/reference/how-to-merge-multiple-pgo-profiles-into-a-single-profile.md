---
title: "如何： 多個 PGO 設定檔合併至單一設定檔 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- merging profiles
- profile-guided optimizations, merging profiles
ms.assetid: aab686b5-59dd-40d1-a04b-5064690f65a6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 880e9fbba7852a9a7919e73f80b73e34394cd037
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-merge-multiple-pgo-profiles-into-a-single-profile"></a>如何：將多個 PGO 設定檔合併至單一設定檔
特性指引最佳化 (PGO) 是用於建立最佳化的二進位檔會分析的案例為基礎的絕佳工具。 但如果您有應用程式，有幾個重要、 但不同的案例;如何建立單一設定檔 PGO 可以使用數個不同的案例？ 在 Visual Studio 中，PGO 管理員 Pgomgr.exe，會為您執行這項作業。  
  
 合併設定檔的語法為：  
  
```  
pgomgr /merge[:num] [.pgc_files] .pgd_files  
```  
  
 其中`num`是用於在此合併選擇性權數。 如果是更重要的是比其他某些情況下，或要多次執行的情況下，常用於加權。  
  
> [!NOTE]
>  PGO 管理員不會使用過時的設定檔資料。 若要合併的.pgc 檔案到.pgd 檔，.pgc 檔案必須產生可執行檔所建立的相同連結引動過程，產生的.pgd 檔。  
  
## <a name="example"></a>範例  
 在此範例中，PGO 管理員將會加入 pgcFile.pgc pgdFile.pgd 六倍。  
  
```  
pgomgr /merge:6 pgcFile.pgc pgdFile.pgd  
```  
  
## <a name="example"></a>範例  
 在此範例中，PGO 管理員將會加入 pgcFile1.pgc 和 pgcFile2.pgc pgdFile.pgd，兩次，每個.pgc 檔案。  
  
```  
pgomgr /merge:2 pgcFile1.pgc pgcFile2.pgc pgdFile.pgd  
```  
  
## <a name="example"></a>範例  
 如果不使用.pgc 檔案執行 PGO 管理員，則它會搜尋所有加上驚嘆號 （！） 後面接著任意字元的.pgd 檔案具有相同名稱的.pgc 檔案的本機目錄。 如果本機目錄含有檔案 test.pgd、 test!1.pgc、 test2.pgc 和 test!hello.pgc，並從本機目錄執行下列命令，然後 test!1.pgc 和 test!hello.pgc 將合併到 test.pgd。  
  
```  
pgomgr /merge test.pgd  
```  
  
## <a name="see-also"></a>請參閱  
 [特性指引最佳化](../../build/reference/profile-guided-optimizations.md)