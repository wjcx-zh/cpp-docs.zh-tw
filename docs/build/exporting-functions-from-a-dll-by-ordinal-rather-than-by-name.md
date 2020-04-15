---
title: 根據序數而不是名稱從 DLL 匯出函式
ms.date: 11/04/2016
helpviewer_keywords:
- exporting functions [C++], ordinal values
- ordinal exports [C++]
- exporting DLLs [C++], ordinal values
- NONAME attribute
ms.assetid: 679719fd-d965-4df3-9f7a-7d86ad831702
ms.openlocfilehash: 66e99b18d181e9067e90398c35a61db2da66c301
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328580"
---
# <a name="exporting-functions-from-a-dll-by-ordinal-rather-than-by-name"></a>根據序數而不是名稱從 DLL 匯出函式

從 DLL 匯出函數的最簡單方法是按名稱匯出它們。 例如,當您使用 **__declspec(dllexport)** 時,就會發生這種情況。 但是,您可以改為按元數匯出函數。 使用此技術,必須使用 .def 檔案而不是 **__declspec(dllexport)**。 要指定函數的元數值,請將其元數追加到 .def 檔中的函數名稱。 有關指定位數的資訊,請參閱[從 DLL 匯出使用 .def 檔案](exporting-from-a-dll-using-def-files.md)。

> [!TIP]
> 如果要優化 DLL 的檔案大小,請使用每個匯出函數上的**NONAME**屬性。 使用**NONAME**屬性時,這些表存儲在 DLL 的匯出表中,而不是函數名稱中。 如果您要匯出許多函數,這可以節省大量成本。

## <a name="what-do-you-want-to-do"></a>您想要做什麼事？

- [使用 .def 檔案,以便我可以透過 ddinal 匯出](exporting-from-a-dll-using-def-files.md)

- [使用__declspec(出口)](exporting-from-a-dll-using-declspec-dllexport.md)

## <a name="see-also"></a>另請參閱

[從 DLL 匯出](exporting-from-a-dll.md)
