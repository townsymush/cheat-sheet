# Formatting

## Adding New line identifiers
This is useful if you need to format a pem file with `/n`

`awk 'NF {sub(/\r/, ""); printf "%s\\n",$0;}' cert.pem`