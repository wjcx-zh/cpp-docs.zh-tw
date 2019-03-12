---
title: UNIX
ms.date: 11/04/2016
f1_keywords:
- unix
helpviewer_keywords:
- UNIX
- POSIX compatibility
- POSIX file names
- UNIX, compatibility
ms.assetid: 40792414-7a5b-415d-bfa8-2bfb1ebb3731
ms.openlocfilehash: edabb639d8f45680415473ad7b017d426b931ab5
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57745244"
---
# <a name="unix"></a>UNIX

若計畫將您的程式移植到 UNIX，請依照這些指導方針執行：

- 不要從 SYS 子目錄移除標頭檔。 只有當您不打算將程式傳輸到 UNIX 時，才可以將 SYS 標頭檔放在其他位置。

- 在接受使用代表路徑與檔案名稱的字串作為引數的常式中使用 UNIX 相容路徑分隔符號。 之對此用途，UNIX 只支援使用斜線 (/)，而 Win32 作業系統同時支援反斜線 (\\) 與斜線 (/)。 因此，此文件使用 UNIX 相容斜線作為 `#include` 陳述式中的路徑分隔符號 (然而，Windows 作業系統命令殼層 (CMD.EXE) 不支援在命令提示字元中輸入命令時使用斜線)。

- 使用可在 UNIX 中正確運作的路徑與檔案名稱 (區分大小寫)。 Win32 作業系統中的檔案配置表 (FAT) 檔案系統不區分大小寫；NTFS 檔案系統會維持目錄清單的大小寫，但在檔案搜尋與其他系統作業中會忽略大小寫。

    > [!NOTE]
    >  在此版本的 Visual C++ 中，我們已從函式描述中移除 UNIX 相容性資訊。

## <a name="see-also"></a>另請參閱

[相容性](../c-runtime-library/compatibility.md)
