# `gentx`

To generate your `gentx` run the following command with the launch genesis file at `~/.injectived/config/genesis.json`:

```bash
    injectived gentx \
      <$VALIDATOR_KEY_NAME> \
      --amount <inj_amount_to_stake> \
      --chain-id="injective-1" \
      --commission-rate <commission_rate> \
      --commission-max-rate <commission_max_rate> \
      --commission-max-change-rate <commission_max_change_rate> \            
      --moniker=<name> \
      --output-document=external-val.json     
```

This will produce a file in the current folder that has a name with the format `external-val.json`. The content of the file should have a structure as follows:


```json
      {
        "body": {
          "messages": [
            {
              "@type": "/cosmos.staking.v1beta1.MsgCreateValidator",
              "description": {
                "moniker": "external-validator",
                "identity": "",
                "website": "",
                "security_contact": "",
                "details": ""
              },
              "commission": {
                "rate": "0.070000000000000000",
                "max_rate": "1.000000000000000000",
                "max_change_rate": "0.010000000000000000"
              },
              "min_self_delegation": "1",
              "delegator_address": "inj1r9rff3kex4rrh3nasltu5vvk7ag439m3d73fan",
              "validator_address": "injvaloper1r9rff3kex4rrh3nasltu5vvk7ag439m36cyvuh",
              "pubkey": {
                "@type": "/cosmos.crypto.ed25519.PubKey",
                "key": "UEWNqoGBVND4ft3QB/MMl17WqEsPI+D8D7iDg4CmC6U="
              },
              "value": {
                "denom": "inj",
                "amount": "90000000000000000000"
              }
            }
          ],
          "memo": "d1fcbaca42af633346ad7a0f9936621a854969b2@192.168.29.80:26656",
          "timeout_height": "0",
          "extension_options": [],
          "non_critical_extension_options": []
        },
        "auth_info": {
          "signer_infos": [
            {
              "public_key": {
                "@type": "/injective.crypto.v1beta1.ethsecp256k1.PubKey",
                "key": "Am5kCK151LodLM+cw6AYOvQ5fb369BS/xq4NvNOMYrOZ"
              },
              "mode_info": {
                "single": {
                  "mode": "SIGN_MODE_DIRECT"
                }
              },
              "sequence": "0"
            }
          ],
          "fee": {
            "amount": [],
            "gas_limit": "200000",
            "payer": "",
            "granter": ""
          }
        },
        "signatures": [
          "eBjti1FfcMVbLS10dOCOVjMZWP7kte857hgZl0b68cddY/N3EgpQFjjVX/5Ywlq/Fc4s0t9WL9MIKbQriHpNQQE="
        ]
    }
```

To submit your `gentx` for inclusion in genesis, open a pull request against this repository and place the contents in a file `/gentx/<moniker>.json`.

__**NOTE**__: If you would like to override the memo field use the `--ip` for the `injectived gentx` command above.
