---
title: "-來源-字元集 （設定來源字元集） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- source-charset
- /source-charset
dev_langs:
- C++
helpviewer_keywords:
- /execution-charset compiler option
ms.assetid: d3c5bf7f-526d-4ee4-acc5-c1a02a4fc481
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a4aa81ba41587a183aca921177a62a45229810f1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="source-charset-set-source-character-set"></a>/source-charset (設定來源 Character Set)
可讓您指定可執行檔的來源字元集。  
  
## <a name="syntax"></a>語法  
  
```  
/source-charset:[IANA_name|.CPID]  
```  
  
## <a name="arguments"></a>引數  
 **IANA_name**  
 IANA 定義字元集名稱。  
  
 **CPID**  
 十進位數字為字碼頁識別項。  
  
## <a name="remarks"></a>備註  
 您可以使用**/source-charset**選項來指定擴充的來源字元設為原始程式檔包含基本來源字元集中未表示的字元時使用。 來源字元集是用來做為輸入之前編譯的前置處理階段的內部表示法解譯之程式的原始程式文字編碼方式。 執行字元集，將字串和字元值儲存在可執行檔的內部表示法會轉換。 您可以使用任一 IANA 或 ISO 字元集的名稱，或點 （.） 後面接著指定要使用的字元集 3 到 5 位數十進位的字碼頁識別項。 一份支援程式碼頁面識別碼和字元集的名稱，請參閱[程式碼頁面識別碼](http://msdn.microsoft.com/library/windows/desktop/dd317756)。  
  
 根據預設，Visual Studio 會偵測來判斷來源檔案是否已編碼的 Unicode 格式，例如，utf-8 或 utf-16 位元組順序標記。 如果找到沒有位元組順序標記，它會假設來源檔案編碼使用目前使用者的字碼頁，除非您指定的字元使用設定名稱或程式碼頁**/source-charset**選項。 Visual Studio 可讓您使用數種字元編碼的任何儲存您的 c + + 程式碼。 如需有關來源和執行字元集的詳細資訊，請參閱[字元集](../../cpp/character-sets2.md)語言文件中。  
  
 您提供的來源字元集必須對應到相同的字碼指標，在字元集中的 7 位元 ASCII 字元，或有可能遵循許多編譯錯誤。 您的來源字元集也必須是可延伸設定 encodable utf-8 的 Unicode 字元對應。 不 encodable utf-8 字元會以實作特定替代。 Microsoft 編譯器會使用問號，這些字元。  
  
 如果您想要設定來源字元集和執行字元集為 utf-8，您可以使用**/utf-8**較快速的編譯器選項。 它相當於指定**/來源-charset:utf-8 /execution-charset:utf-8**命令列上。 這些選項也可讓**/validate-charset**預設選項。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  展開**組態屬性**， **C/c + +**，**命令列**資料夾。  
  
3.  在**進階選項**，新增**/source-charset**選項，並指定您的慣用編碼方式。  
  
4.  選擇**確定**以儲存變更。  
  
## <a name="see-also"></a>請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [/execution-charset (設定執行 Character Set)](../../build/reference/execution-charset-set-execution-character-set.md)   
 [/utf-8 （設定來源和可執行檔字元集為 utf-8）](../../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)   
 [/validate-charset （驗證相容的字元）](../../build/reference/validate-charset-validate-for-compatible-characters.md)