Receiving

## ASN Clean-Up Project

```sql
SELECT AHASTP AS ASNType,AHSHMT AS ASN,AHFRDT AS FirstReceiptDate,
AHFRTM AS FirstReceiptTime,AHLRDT AS LastReceiptDate,AHLRTM AS LastReceiptTime,AHSTAT AS Status FROM WM370BASD.AHASNF00
JOIN WM370BASD.ADASNF00 ON ADSHMT=AHSHMT WHERE AHSHMT='1350512285' AND substr(ADSTYL,1,4)='EHHT';

--Statement to show Ingram ASNs that are still open beyond a certain date (Non-Grommet)
--UPDATE WM370BASD.AHASNF00 SET AHSTAT='90' WHERE AHSHMT IN
(SELECT AHSHMT AS ASN FROM WM370BASD.AHASNF00 JOIN WM370BASD.ADASNF00 ON ADSHMT=AHSHMT
WHERE AHSTAT='10' AND AHDCR<'20210101' AND AHDLM<'20210101' AND ADCO='2102' AND substr(ADSTYL,1,4)<>'EHHT'ORDER BY 1);

SELECT ADSHMT,ADMIS1,ADMIS2,ADMIS3,ADMIS4 FROM WM370BASD.ADASNF00
WHERE ADMIS1<>'' OR ADMIS2<>'' OR ADMIS3<>'' OR ADMIS4<>'';
```

