---
title: 使用 INSERT 載入資料
description: 使用 T-sql INSERT 語句，將資料載入至平行處理資料倉儲（PDW）分散式或複寫資料表。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: bbcf1a8bd16d7446841bb6d7dd86bd1ad350280d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "74401024"
---
# <a name="load-data-with-insert-into-parallel-data-warehouse"></a>使用 INSERT 將資料載入平行處理資料倉儲

您可以使用 tsql INSERT 語句，將資料載入至 SQL Server 平行處理資料倉儲（PDW）分散式或複寫資料表。 如需 INSERT 的詳細資訊，請參閱[insert](../t-sql/statements/insert-transact-sql.md)。 針對複寫資料表和分散式資料表中的所有非散發資料行，PDW 會使用 SQL Server，將語句中指定的資料值隱含轉換為目的地資料行的資料類型。 如需 SQL Server 資料轉換規則的詳細資訊，請參閱[SQL 的資料類型轉換](../t-sql/data-types/data-type-conversion-database-engine.md)。 不過，針對散發資料行，PDW 僅支援 SQL Server 支援的隱含轉換子集。 因此，當您使用 INSERT 語句將資料載入散發資料行時，來源資料必須以下表中定義的其中一種格式來指定。  
  
  
## <a name="insert-literals-into-binary-types"></a><a name="InsertingLiteralsBinary"></a>將常值插入二進位類型  
下表定義接受的常數值型別、格式和轉換規則，用於將常值插入**binary**類型的散發資料行（*n*）或**Varbinary**（*n*）。  
  
|常值型別|[格式]|轉換規則|  
|----------------|----------|--------------------|  
|二進位常值|0x*hexidecimal_string*<br /><br />範例：0x12Ef|二進位常值的前面必須加上0x。<br /><br />資料來源長度不能超過為資料類型所指定的位元組數目。<br /><br />如果資料來源長度小於**二進位**資料類型的大小，資料會向右填補，而零會到達資料類型大小。|  
  
## <a name="insert-literals-into-date-and-time-types"></a><a name="InsertingLiteralsDateTime"></a>將常值插入日期和時間類型  
日期和時間常值是使用特定格式的字元值來表示，並以單引號括住。 下表定義允許的常數值型別、格式和轉換規則，用於將日期或時間常值插入**datetime**、 **Smalldatetime**、 **date**、 **time**、 **datetimeoffset**或**datetime2**類型的 SQL Server PDW 散發資料行中。  
  
### <a name="datetime-data-type"></a>datetime 資料類型  
下表定義接受的格式，以及將常值插入**datetime**類型之散發資料行的規則。 任何空字串（' '）都會轉換成預設值 ' 1900-01-01 12：00： 00.000 '。 只包含空格（' '）的字串會產生錯誤。  
  
|常值型別|[格式]|轉換規則|  
|----------------|----------|--------------------|  
|**日期時間**格式的字串常值|' YYYY-MM-DD hh： MM： ss [. nnn] '<br /><br />範例： ' 2007-05-08 12：35： 29.123 '|插入值時，遺失的小數位數會設定為0。 例如，常值 ' 2007-05-08 12:35 ' 會插入為 ' 2007-05-08 12：35： 00.000 '。|  
|**Smalldatetime**格式的字串常值|' YYYY-MM-DD hh： MM '<br /><br />範例： ' 2007-05-08 12:35 '|插入值時，秒數和剩餘小數數位會設定為0。|  
|**日期**格式的字串常值|' YYYY-MM-DD '<br /><br />範例： ' 2007-05-08 '|插入值時，時間值（小時、分鐘、秒和分數）會設定為12：00：00.000。|  
|**Datetime2**格式的字串常值|' YYYY-MM-DD hh： MM： ss. nnnnnnn '<br /><br />範例： ' 2007-05-08 12：35： 29.1234567 '|來源資料不能超過三個小數位數。 例如，將會插入常值 ' 2007-05-08 12：35： 29.123 '，但值 ' 2007-05-08 12：35： 29.1234567 ' 會產生錯誤。|  
  
### <a name="smalldatetime-data-type"></a>smalldatetime 資料類型  
下表定義接受的格式，以及將常值插入至**Smalldatetime**類型之散發資料行的規則。 任何空字串（' '）都會轉換成預設值 ' 1900-01-01 12:00 '。 只包含空格（' '）的字串會產生錯誤。  
  
|常值型別|[格式]|轉換規則|  
|----------------|----------|--------------------|  
|**Smalldatetime**格式的字串常值|' YYYY-MM-DD hh： mm ' 或 ' YYYY-MM-DD hh： mm： 00 '<br /><br />範例： ' 2007-05-08 12:00 ' 或 ' 2007-05-08 12:00:00 '|來源資料必須具有 year、month、date、hour 和 minute 的值。 秒是選擇性的，如果存在，則必須設為值00。 任何其他值都會產生錯誤。|  
|**日期**格式的字串常值|' YYYY-MM-DD '<br /><br />範例： ' 2007-05-08 '|插入值時，時間值（小時、分鐘、秒和分數）會設定為0。|  
  
### <a name="date-data-type"></a>date 資料類型  
下表定義接受的格式，以及將常值插入**date**類型之散發資料行的規則。 任何空字串（' '）都會轉換成預設值 ' 1900-01-01 '。 只包含空格（' '）的字串會產生錯誤。  
  
|常值型別|[格式]|轉換規則|  
|----------------|----------|--------------------|  
|**日期**格式的字串常值|' YYYY-MM-DD '<br /><br />範例： ' 2007-05-08 '|這是唯一接受的格式。|  
  
### <a name="time-data-type"></a>time 資料類型  
下表定義接受的格式，以及將常值插入至**time**類型之散發資料行的規則。 任何空字串（' '）都會轉換成預設值 ' 00：00： 00.0000 '。 只包含空格（' '）的字串會產生錯誤。  
  
|常值型別|[格式]|轉換規則|  
|----------------|----------|--------------------|  
|**時間**格式的字串常值|' hh： mm： ss. nnnnnnn '<br /><br />範例： ' 12：35： 29.1234567 '|如果資料來源的精確度小於或等於**時間**資料類型的有效位數，則資料會以零填補到右邊。 例如，常值 ' 12：35： 29.123 ' 會插入為 ' 12：35： 29.1230000 '。<br /><br />具有比目標資料類型更大的有效位數的值會遭到拒絕。|  
  
### <a name="datetimeoffset-data-type"></a>datetimeoffset 資料類型  
下表定義接受的格式，以及將常值插入至類型**datetimeoffset** （*n*）之散發資料行的規則。 預設格式為 ' YYYY-MM-DD hh： mm： ss. nnnnnnn {+ |-} hh： mm '。 空字串（' '）會轉換成預設值 ' 1900-01-01 12：00： 00.0000000 + 00:00 '。 只包含空格（' '）的字串會產生錯誤。 小數數位的數目取決於資料行定義。 例如，定義為**datetimeoffset** （2）的資料行將會有兩個小數位數。  
  
|常值型別|[格式]|轉換規則|  
|----------------|----------|--------------------|  
|**日期時間**格式的字串常值|' YYYY-MM-DD hh： MM： ss [. nnn] '<br /><br />範例： ' 2007-05-08 12：35： 29.123 '|插入值時，遺失的小數位數和位移值會設為0。 例如，常值 ' 2007-05-08 12：35： 29.123 ' 會插入為 ' 2007-05-08 12：35： 29.1230000 + 00:00 '。|  
|**Smalldatetime**格式的字串常值|' YYYY-MM-DD hh： MM '<br /><br />範例： ' 2007-05-08 12:35 '|秒，插入值時，剩餘的小數位數和位移值都會設定為0。|  
|**日期**格式的字串常值|' YYYY-MM-DD '<br /><br />範例： ' 2007-05-08 '|插入值時，時間值（小時、分鐘、秒和分數）會設定為0。 例如，常值 ' 2007-05-08 ' 會插入為 ' 2007-05-08 00：00： 00.0000000 + 00:00 '。|  
|**Datetime2**格式的字串常值|' YYYY-MM-DD hh： MM： ss. nnnnnnn '<br /><br />範例： ' 2007-05-08 12：35： 29.1234567 '|來源資料不能超過 datetimeoffset 資料行中指定的小數秒數。 如果資料來源的小數秒數較小或相等，資料會向右填補零。 例如，如果資料類型為 datetimeoffset （5），則常值 ' 2007-05-08 12：35： 29.123 + 12:15 ' 會插入為 ' 12：35： 29.12300 + 12:15 '。|  
|**Datetimeoffset**格式的字串常值|' YYYY-MM-DD hh： mm： ss. nnnnnnn {+&#124;-} hh： mm '<br /><br />範例： ' 2007-05-08 12：35： 29.1234567 + 12:15 '|來源資料不能超過 datetimeoffset 資料行中指定的小數秒數。 如果資料來源的小數秒數較小或相等，資料會向右填補零。 例如，如果資料類型為 datetimeoffset （5），則常值 ' 2007-05-08 12：35： 29.123 + 12:15 ' 會插入為 ' 12：35： 29.12300 + 12:15 '。|  
  
### <a name="datetime2-data-type"></a>datetime2 資料類型  
下表定義接受的格式，以及將常值插入至**datetime2**類型之散發資料行的規則*n*。 預設格式為 ' YYYY-MM-DD hh： MM： ss. nnnnnnn '。 空字串（' '）會轉換成預設值 ' 1900-01-01 12:00:00 '。 只包含空格（' '）的字串會產生錯誤。 小數數位的數目取決於資料行定義。 例如，定義為**datetime2** （2）的資料行將會有兩個小數位數。  
  
|常值型別|[格式]|轉換規則|  
|----------------|----------|--------------------|  
|**日期時間**格式的字串常值|' YYYY-MM-DD hh： MM： ss [. nnn] '<br /><br />範例： ' 2007-05-08 12：35： 29.123 '|小數秒是選擇性的，而且會在插入值時設定為0。<br /><br />具有比目標資料類型更多之小數位數的值會遭到拒絕。|  
|**Smalldatetime**格式的字串常值|' YYYY-MM-DD hh： MM '<br /><br />範例： ' 2007-05-08 12 '|插入值時，選擇性的秒數和剩餘的小數數位都會設定為0。|  
|**日期**格式的字串常值|' YYYY-MM-DD '<br /><br />範例： ' 2007-05-08 '|插入值時，時間值（小時、分鐘、秒和分數）會設定為0。 例如，常值 ' 2007-05-08 ' 會插入為 ' 2007-05-08 12：00： 00.0000000 '。|  
|**Datetime2**格式的字串常值|' YYYY-MM-DD hh： MM： ss： nnnnnnn '<br /><br />範例： ' 2007-05-08 12：35： 29.1234567 '|如果資料來源包含的資料和時間元件小於或等於**datetime2**（*n*）中指定的值，則會插入資料;否則會產生錯誤。|  
  
## <a name="insert-literals-into-numeric-types"></a><a name="InsertLiteralsNumeric"></a>將常值插入數數值型別  
下表定義接受的格式和轉換規則，用於將常值插入至使用數數值型別的 SQL Server PDW 散發資料行。  
  
### <a name="bit-data-type"></a>bit 資料類型  
下表定義接受的格式，以及將常值插入**bit**類型之散發資料行的規則。 空字串（' '）或只包含空白（' '）的字串會轉換為0。  
  
|常值型別|format|轉換規則|  
|----------------|----------|--------------------|  
|**整數**格式的字串常值|'nnnnnnnnnn'<br /><br />範例： ' 1 ' 或 ' 321 '|格式化為字串常值的整數值不能包含負值。 例如，值 '-123 ' 會產生錯誤。<br /><br />大於1的值會轉換成1。 例如，值 ' 123 ' 會轉換成1。|  
|字串常值|' TRUE ' 或 ' FALSE '<br /><br />範例： ' true '|值 ' TRUE ' 轉換成 1;值 ' FALSE ' 會轉換為0。|  
|整數常值|nnnnnnnn<br /><br />範例：1或321|大於1或小於0的值會轉換成1。 例如，值123和-123 會轉換成1。|  
|十進位常值|nnnnn nnnn<br /><br />範例：1234.5678|大於1或小於0的值會轉換成1。 例如，值123.45 和-123.45 會轉換成1。|  
  
### <a name="decimal-data-type"></a>十進位資料類型  
下表定義接受的格式，以及將常值插入**decimal** （*p，s*）類型之散發資料行的規則。 資料轉換規則與 SQL Server 相同。 如需詳細資訊，請參閱 MSDN 上的[資料類型轉換](../t-sql/data-types/data-type-conversion-database-engine.md)。  
  
|常值型別|[格式]|  
|----------------|----------|  
|**整數**格式的字串常值|'nnnnnnnnnnnn'<br /><br />範例： ' 321312313123 '|  
|**十進位**格式的字串常值|' nnnnnn. nnnnn '<br /><br />範例： ' 123344.34455 '|  
|整數常值|nnnnnnnnnnnn<br /><br />範例：321312313123|  
|十進位常值|nnnnnn. nnnnn<br /><br />範例： ' 123344.34455 '|  
  
### <a name="float-and-real-data-types"></a>float 和 real 資料類型  
下表定義接受的格式和規則，可將常值插入**float**或**real**類型的散發資料行中。 資料轉換規則與 SQL Server 相同。 如需詳細資訊，請參閱 MSDN 上的[資料類型轉換](../t-sql/data-types/data-type-conversion-database-engine.md)。  
  
|常值型別|[格式]|  
|----------------|----------|  
|**整數**格式的字串常值|'nnnnnnnnnnnn'<br /><br />範例： ' 321312313123 '|  
|**十進位**格式的字串常值|' nnnnnn. nnnnn '<br /><br />範例： ' 123344.34455 '|  
|**浮點**格式的字串常值|' n. nnnnnE + nn '<br /><br />範例： ' 3.12323 E + 14 '|  
|整數常值|nnnnnnnnnnnn<br /><br />範例：321312313123|  
|十進位常值|nnnnnn. nnnnn<br /><br />範例：123344.34455|  
|浮點常值|n. nnnnnE + nn<br /><br />範例： 3.12323 E + 14|  
  
### <a name="int-bigint-tinyint-smallint-data-types"></a>int、Bigint、Tinyint、Smallint 資料類型  
下表定義接受的格式和規則，可將常值插入**int**、 **Bigint**、 **Tinyint**或**Smallint**類型的散發資料行中。 資料來源不能超過給定資料類型所允許的範圍。 例如， **Tinyint**的範圍是0到255，而**int**的範圍是-2147483648 到2147483647。  
  
|常值類型|[格式]|轉換規則|  
|------------|------|----------------|
|**整數**格式的字串常值|'nnnnnnnnnnnnnn'<br /><br />範例： ' 321312313123 '| None |  
|整數常值|nnnnnnnnnnnnnn<br /><br />範例：321312313123| None|  
|十進位常值|nnnnnn. nnnnn<br /><br />範例：123344.34455|小數點右邊的值會被截斷。|  
  
### <a name="money-and-smallmoney-data-types"></a>money 和 smallmoney 資料類型  
Money 常值會以數位表示，並以選擇性的小數點和貨幣符號做為前置詞。 資料來源不能超過給定資料類型所允許的範圍。 例如， **smallmoney**的範圍是-214748.3648 到214748.3647，而**money**的範圍是-922337203685477.5808 到922337203685477.5807。 下表定義接受的格式和規則，用於將常值插入**money**或**smallmoney**類型的散發資料行中。  
  
|常值型別|[格式]|轉換規則|  
|----------------|----------|--------------------|  
|**整數**格式的字串常值|nnnnnnnn<br /><br />範例： ' 123433 '|當插入值時，小數點之後遺失的數位會設定為0。 例如，常值 ' 12345 ' 會插入為12345.0000。|  
|**十進位**格式的字串常值|' nnnnnn. nnnnn '<br /><br />範例： ' 123344.34455 '|如果小數點後的位數超過4，此值會無條件進位到最接近的值。 例如，值 ' 123344.34455 ' 會插入為123344.3446。|  
|**貨幣**格式的字串常值|' $nnnnnn nnnn '<br /><br />範例： ' $123456.7890 '|選擇性貨幣符號不會插入值。<br /><br />如果小數點後的位數超過4，此值會無條件進位到最接近的值。|  
|整數常值|nnnnnnnn<br /><br />範例：123433|當插入值時，小數點之後遺失的數位會設定為0。 例如，常值12345會插入為12345.0000。|  
|十進位常值|nnnnnn. nnnnn<br /><br />範例：123344.34455|如果小數點後的位數超過4，此值會無條件進位到最接近的值。 例如，值123344.34455 會插入為123344.3446。|  
|Money 常值|$nnnnnn nnnn<br /><br />範例： $123456.7890|選擇性貨幣符號不會插入值。<br /><br />如果小數點後的位數超過4，此值會無條件進位到最接近的值。|  
  
## <a name="inserting-literals-into-string-types"></a><a name="InsertLiteralsString"></a>將常值插入字串類型  
下表定義接受的格式和轉換規則，將常值插入至使用字串類型的 SQL Server PDW 資料行中。  
  
### <a name="char-varchar-nchar-and-nvarchar-data-types"></a>char、Varchar、Nchar 和 Nvarchar 資料類型  
下表定義接受的格式，以及將常值插入**char**、 **Varchar**、 **Nchar**和**Nvarchar**類型之散發資料行的規則。 資料來源長度不能超過針對資料類型所指定的大小。 如果資料來源長度小於**char**或**Nchar**資料類型的大小，資料就會以空格填補至右邊，以達到資料類型大小。  
  
|常值類型|[格式]|轉換規則|  
|----------------|----------|--------------------|  
|字串常值|格式： ' 字元字串 '<br /><br />範例： ' abc '| None|  
|Unicode 字串常值|格式： N'character 字串 '<br /><br />範例： N'abc '|  None |  
|整數常值|格式： nnnnnnnnnnn<br /><br />範例：321312313123| None |  
|十進位常值|格式： nnnnnn. nnnnnnn<br /><br />範例：12344.34455| None |  
|Money 常值|格式： $nnnnnn. nnnnn<br /><br />範例： $123456.99|不會使用值插入貨幣符號。 若要插入貨幣符號，請將值插入為字串常值。 這會符合**dwloader**工具的格式，其會將每個常值視為字串常值。<br /><br />不允許使用逗號。<br /><br />如果小數點後的位數超過2，此值會無條件進位到最接近的值。 例如，值123.946789 會插入為123.95。<br /><br />使用 CONVERT 函式插入 money 常值時，只允許預設樣式0（小數點後面沒有逗號和2位數）。|  

  
## <a name="see-also"></a>另請參閱  
 
[分散式資料](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-distributed-data/)  
[插入](../t-sql/statements/insert-transact-sql.md)  
  
<!-- MISSING LINKS
[Grant permissions to load data](grant-permissions-to-load-data.md)  
[Metadata query examples](metadata-query-examples.md) 
-->
