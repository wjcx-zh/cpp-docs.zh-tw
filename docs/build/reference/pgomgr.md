---
title: pgomgr |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- pgomgr program
- profile-guided optimizations, pgomgr
ms.assetid: 74589126-df18-42c9-8739-26d60e148d6a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 217346a08f4dc800c3d335baa77c355e0f327336
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44105311"
---
# <a name="pgomgr"></a>pgomgr

將設定檔資料從一或多個的.pgc 檔案加入至.pgd 檔。

## <a name="syntax"></a>語法

> **pgomgr** [*options*] *pgcfiles* *pgdfile*

### <a name="parameters"></a>參數

*options*<br/>
下列選項可指定來**pgomgr**:

- **/help**或 **/？** 顯示可用**pgomgr**選項。

- **清除/** 會導致要清除的所有設定檔資訊的.pgd 檔案。 您無法指定.pgc 檔案時 **/清除**指定。

- **/detail**顯示詳細的統計資料，包括流程圖形的涵蓋範圍資訊。

- **摘要/** 顯示每個函式的統計資料。

- **/ 唯一**搭配使用時 **/summary>**，原因裝飾函式名稱來顯示。 預設值，當 **/ 唯一**未使用，是要顯示的未裝飾的函式名稱。

- **/ merge**\[**:**<em>n</em>] 會導致資料中要加入至.pgd 檔的.pgc 檔案。 將選擇性參數*n*，可讓您指定的資料應該加入*n*時間。 比方說，如果案例通常是以反映方式通常它由客戶完成的六倍，可以一次在測試回合中執行並將它加入至.pgd 檔案六倍**pgomgr /merge:6**。

*pgcfiles*<br/>
一或多個的.pgc 檔案您想要合併的.pgd 檔的設定檔資料。 您可以指定單一的.pgc 檔案或多個的.pgc 檔案。 如果您未指定任何的.pgc 檔案**pgomgr**合併所有的檔案名稱是.pgd 檔相同的.pgc 檔案。

*pgdfile*<br/>
.Pgd 檔案，其中您要合併的.pgc 檔案或檔案中的資料。

## <a name="remarks"></a>備註

> [!NOTE]
> 您可以啟動此工具只能從 Visual Studio 開發人員命令提示字元。 您無法從系統命令提示字元，或從 [檔案總管] 啟動它。

## <a name="example"></a>範例

此範例命令會清除 myapp.pgd 檔的設定檔資料：

`pgomgr /clear myapp.pgd`

此範例命令將設定檔資料中 myapp1.pgc 至.pgd 檔三次：

`pgomgr /merge:3 myapp1.pgc myapp.pgd`

在此範例中，所有的 myapp #.pgc 檔案中的設定檔資料會加入 myapp.pgd 檔案。

`pgomgr -merge myapp1.pgd`

## <a name="see-also"></a>另請參閱

[特性指引最佳化](profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>
[pgosweep](pgosweep.md)<br/>
