---
title: 建置匯入程式庫和匯出檔案
ms.date: 09/05/2018
f1_keywords:
- VC.Project.VCLibrarianTool.ModuleDefinitionFile
- VC.Project.VCLibrarianTool.ExportNamedFunctions
- VC.Project.VCLibrarianTool.GenerateDebug
- VC.Project.VCLibrarianTool.ForceSymbolReferences
helpviewer_keywords:
- OUT library manager option
- INCLUDE library manager option
- /DEF library manager option
- exporting data
- import libraries, building
- -INCLUDE library manager option
- /OUT library manager option
- DEF library manager option
- -DEF library manager option
- -OUT library manager option
- /INCLUDE library manager option
- -EXPORT library manager option
- exporting data, export (.exp) files
- /EXPORT library manager option
- EXPORT library manager option
- .lib files
- EXP files
ms.assetid: 2fe4f30a-1dd6-4b05-84b5-0752e1dee354
ms.openlocfilehash: 5cb5224b3edaf84dbcb7c0429044a647fb5ac19a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229749"
---
# <a name="building-an-import-library-and-export-file"></a>建置匯入程式庫和匯出檔案

若要建立匯入程式庫和匯出檔案，請使用下列語法：

> **LIB/DEF**[**：**<em>deffile</em>] [*選項*] [*objfiles*] [連結*庫*]

當指定/DEF 時，LIB 會從在 LIB 命令中傳遞的匯出規格建立輸出檔案。 有三種方法可以指定匯出，並以建議的使用順序列出：

1. **`__declspec(dllexport)`** 其中一個*objfiles*或連結*庫*中的定義

1. LIB 命令列上的/EXPORT：*name*規格

1. *Deffile*中**匯出**語句的定義

這些是您在連結匯出程式時用來指定匯出的相同方法。 程式可以使用一種以上的方法。 您可以在 LIB 命令的命令檔中指定 LIB 命令的各個部分（例如多個*objfiles*或/export 規格），就如同您在 LINK 命令中所做的一樣。

下列選項適用于建立匯入程式庫和匯出檔案：

> **/Out：** 匯*入*

覆寫所建立之匯*入*程式庫的預設輸出檔案名。 未指定/OUT 時，預設名稱會是 LIB 命令中第一個物件檔案或程式庫的基底名稱，以及副檔名 .lib。 匯出檔案的基底名稱與匯入程式庫和副檔名 .exp 相同。

> **/Export：** *entryname* \[ **=** *internalname*] \[ ， **\@** <em>序數</em> \[ ， **NONAME**]] \[ ， **DATA**]

從您的程式匯出函式，以允許其他程式呼叫函式。 您也可以匯出資料（使用**data**關鍵字）。 匯出通常是在 DLL 中定義。

*Entryname*是呼叫程式所要使用的函式或資料項目的名稱。 （選擇性）您可以將*internalname*指定為定義程式中已知的函式;根據預設， *internalname*與*entryname*相同。 *序數*會指定匯出資料表的索引，範圍介於1到 65535;如果您未指定*序數*，LIB 會指派一個。 **NONAME**關鍵字只會將函數匯出為序數，而不會有*entryname*。 **Data**關鍵字是用來匯出僅限資料的物件。

> **/INCLUDE：** *符號*

將指定的*符號*加入至符號表。 此選項適用于強制使用原本不會包含的程式庫物件。

請注意，如果您在初步步驟中建立匯入程式庫，在建立 .dll 之前，您必須在建立 .dll 時傳遞一組相同的物件檔，如同您在建立匯入程式庫時所傳遞的一樣。

## <a name="see-also"></a>另請參閱

[使用匯入程式庫和匯出檔案](working-with-import-libraries-and-export-files.md)
