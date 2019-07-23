---
title: 二進位輸出檔案
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [C++], binary output files
- files [C++], binary output files
- binary data, binary output files
ms.assetid: 180954af-8cd6-444b-9a76-2f630a3389d8
ms.openlocfilehash: 4562f5c1167aeadc6689313e73545ed1ad9bbcf8
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2019
ms.locfileid: "68376340"
---
# <a name="binary-output-files"></a>二進位輸出檔案

資料流最初是針對文字所設計，因此預設輸出模式是文字。 在文字模式中, 換行字元 (分行符號) 會展開為一組換行的回車。 此擴充可能造成問題，如下所示：

```cpp
// binary_output_files.cpp
// compile with: /EHsc
#include <fstream>
using namespace std;
int iarray[2] = { 99, 10 };
int main( )
{
    ofstream os( "test.dat" );
    os.write( (char *) iarray, sizeof( iarray ) );
}
```

您可能預期此程式輸出位元組序列 { 99, 0, 10, 0 }，但它卻輸出 { 99, 0, 13, 10, 0 }，導致預期二進位輸入的程式出現問題。 如果您需要真正的二進位輸出 (在其中寫入未轉譯的字元), 您可以使用[ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream)的函數`openmode`引數來指定二進位輸出:

```cpp
// binary_output_files2.cpp
// compile with: /EHsc
#include <fstream>
using namespace std;
int iarray[2] = { 99, 10 };

int main()
{
   ofstream ofs ( "test.dat", ios_base::binary );

   // Exactly 8 bytes written
   ofs.write( (char*)&iarray[0], sizeof(int)*2 );
}
```

## <a name="see-also"></a>另請參閱

[輸出資料流](../standard-library/output-streams.md)
