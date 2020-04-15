---
title: /SOURCELINK (在 PDB 中納入 Sourcelink 檔案)
description: 微軟C++/SOURCELINK連結器選項的參考指南。
ms.date: 03/31/2020
f1_keywords:
- /sourcelink
helpviewer_keywords:
- /SOURCELINK linker option
- /SOURCELINK
ms.openlocfilehash: bde55c401e17f7b3c84ffcdad29dda2badcc260b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336060"
---
# <a name="sourcelink-include-source-link-file-in-pdb"></a>/SOURCELINK(在 PDB 中包括源連結檔案)

指定要包含在連結器生成的 PDB 檔中的來源連結設定檔。

## <a name="syntax"></a>語法

> **`/SOURCELINK:`**_`filename`_

## <a name="arguments"></a>引數

*檔案名稱*<br/>
指定 JSON 格式的設定檔,該檔包含本地端檔案路徑的簡單映射到 URL,以便源檔在除錯器中顯示。 有關此檔案格式的詳細資訊,請參閱[源連結 JSON 架構](https://github.com/dotnet/designs/blob/master/accepted/2020/diagnostics/source-link.md#source-link-json-schema)。

## <a name="remarks"></a>備註

源連結是一個語言和原始程式碼管理無關的系統,用於為二進位檔案提供源調試。 源連結支援從 Visual Studio 2017 版本 15.8 開始的本機C++二進位檔。 有關源連結的概述,請參閱[源連結](https://github.com/dotnet/designs/blob/master/accepted/2020/diagnostics/source-link.md)。 有關如何在專案中使用來源連結以及如何將 SourceLink 檔產生作為專案的一部分的資訊,請參閱[使用來源連結](https://github.com/dotnet/sourcelink#using-source-link-in-c-projects)。

### <a name="to-set-the-sourcelink-linker-option-in-visual-studio"></a>在視覺化工作室中設定 /SOURCELINK 連結器選項

1. 打開項目**的屬性頁**對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選擇**設定屬性** > **連結器** > **命令列**屬性頁。

1. 在「**其他選項**」框中,**`/SOURCELINK:`**_`filename`_ 新增然後選擇 **「確定」** 或 **「應用」** 以儲存變更。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 此選項沒有程式設計等效項。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
