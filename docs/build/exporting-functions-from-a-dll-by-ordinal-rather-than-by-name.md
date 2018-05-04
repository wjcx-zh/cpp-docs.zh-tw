---
title: 匯出函式從 DLL 依序數，而不是依名稱 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- NONAME
dev_langs:
- C++
helpviewer_keywords:
- exporting functions [C++], ordinal values
- ordinal exports [C++]
- exporting DLLs [C++], ordinal values
- NONAME attribute
ms.assetid: 679719fd-d965-4df3-9f7a-7d86ad831702
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b05f3e429406b3c24c7a21ce9ee8e10fe19c14b8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="exporting-functions-from-a-dll-by-ordinal-rather-than-by-name"></a>根據序數而不是名稱從 DLL 匯出函式
從您的 DLL 匯出函式最簡單的方式是將它們匯出的名稱。 這是當您使用時，會發生什麼事 **__declspec （dllexport)**，例如。 但是，您可以依序數匯出函式。 使用這項技巧，您必須使用.def 檔案，而不是 **__declspec （dllexport)**。 若要指定函式的序數值，將附加至.def 檔案中的函式名稱的其序數。 指定序數的相關資訊，請參閱[使用.def 檔從 DLL 匯出](../build/exporting-from-a-dll-using-def-files.md)。  
  
> [!TIP]
>  如果您想要最佳化您的 DLL 檔案的大小，使用**NONAME**上每個匯出的函式的屬性。 與**NONAME**屬性，序數的資料會儲存在 DLL 的匯出資料表，而不是函式名稱。 如果您要匯出的許多功能，這可能會相當大的節省量。  
  
## <a name="what-do-you-want-to-do"></a>請您指定選項。  
  
-   [使用.def 檔，所以我可以匯出依序數](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [使用 __declspec （dllexport）](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
## <a name="see-also"></a>另請參閱  
 [從 DLL 匯出](../build/exporting-from-a-dll.md)