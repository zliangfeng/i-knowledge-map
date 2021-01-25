## refs

## contents
- Unicode：双字节编码所有字符
- utf8: Unicode transfer format，原ascii不变，n（n大于1）个字节的字符，第一个子节的前n位设1，n+1位舍0（分隔标识位），后面两位字节前2bit设10，其余用Unicode填充，高位0补足；中文字符用三子节编码
- varchar：英文800，中文400，
- nvarchar：使用Unicode编码，最大字符400