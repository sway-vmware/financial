# Sheet User Instructions

User documentation for the worksheet. This aims to be a hand-held step-by-step for how to gather the necessary documents, extract the information from them, and add it into the worksheet, chose any optional values, and then understand the result.

For how to access the worksheet, see [the readme install section](https://github.com/hickeng/financial?tab=readme-ov-file#install)

# Inputs

This section is about getting all of the input data needed. Once gathered, you should back this up and keep it in case of future reference.

## Gathering documents from eTrade

There's various documents we need to export from eTrade.

### eTrade Stock Plan Confirmations

Gather the ESPP purchase confirmation, and RSU release confirmation documents for every lot for which you still own any shares from [the trade confirmations page](https://us.etrade.com/etx/sp/stockplan#/myAccount/stockPlanConfirmations). I don't know a better way than selecting each year in turn and clicking on the download links. If anyone finds a way to batch this, please let me know.

![etrade trade confirmations download page with relevant areas highlighted](assets/etrade-confirmations-highlighted.png)

Keep these for your records and back them up somewhere. They are THE definitive input into the entire process. Everything else can be reconstructed if you have these.

If you sold AVGO post-merger in 2023, you'll likely need to use the tradesdownload.csv to populate the worksheet `Share amounts from eTrade` column


### eTrade transaction log

Use [the eTrade transaction log](https://us.etrade.com/e/t/accounts/txnhistory) (filter for entries relating to acquisition, propably between 2023-11-21 and 2023-12-09) to retrieve:
* VMW shares converted to AVGO (green)
* VMW shares exchanged for cash (blue)
* total cash consideration recieved (dark red)
* total AVGO received (red)
* fractional AVGO sale price (orange)

![Transaction log annotated with values to enter into sheet](assets/etrade-transaction-log-annotated.png)


These values should be entered into the worksheet Input section on the `Summary` sheet. The VMW shares exchange for XXX are used to determine the specific conversion ratio that applied to you, which is used to calculate the per-lot quantities for cash and AVGO.

The other values are used for validation as, with just the ratio and the number of shares for each lot, we expect the numbers to match up.

![Colour coded Input section for worksheet](assets/sheet-summary-colour-coded-inputs.png)


### eTrade per-lot AVGO quantities

Go to etrade `Stock Plan->My Account->Benefit History` and look at the `OSPS` section:
* for each lot, take the `Acquired Qty.` (orange) and add it into the worksheet (details below)
* the `Total Acquired Qty.` (red) should match the number of AVGO you received in the transaction log and entered into

![screenshot showing where to find quantities of AVGO after conversion ](assets/etrade-benefit-history-osps-highlighted.png)

For each lot I see it bracketed with a pair of 0 qty lots. I _presume_ these come from the various holding company transitions that occurred as part of the conversion from `VMW->Holding1->Holding2->AVGO`... regardless I've ignored them.

Enter these received quantities into the `Share amounts from eTrade` column in ESPP and RSU sheets. Be sure to match them up to the appropriate row in the sheet if using the sheet to save these values using the `Purchase Date`.

If you had a fractional share, you'll be adjusting one of these values to add it back later, once the lot it came from has been determined.

![screenshot of the ESPP sheet with shares from etrade highlighted](assets/sheet-espp-shares-from-etrade-highlight.png)

)


### eTrade 1099-B & Supplement

We need to get per-lot details from the eTrade 1099-B document for 2023. For completeness you'll want the Supplement and the CSV export of your trades for 2023 tax year. If you sold VMW pre-acquisition, or AVGO post-acquisition _I expect_ them to show up in the csv, but cannot confirm personally. Keep these for your records.

These documents can be found in the [eTrade Tax Center](https://us.etrade.com/etx/pxy/tax-center?resource=stock-plan).
![eTrade tax center screenshot with relevant links highlighted](assets/etrade-tax-center-highlighted.png)


It will contain some summary information that we don't need. What we need is the per-lot details found in `PROCEEDS FROM BROKER AND BARTER EXCHANGE TRANSACTIONS`
![Section header](assets/1099-b-section-header.png)

Within there, there may be multiple different subsections. We only care about these groupings because it makes it easier to figure out whether it's an ESPP or RSU lot:
* `Short Term - Noncovered Securities` - RSU from 2023
* `Long Term - Noncovered Securities` - RSU from pre-2023
* `Long Term - Covered Securities` - ESPP (the final ESPP lot was 2022 so they'll all be here)

Each of those sections has the following fields:
![Detail headings](assets/1099-b-detail-headings.png)

We're only interested in VMW shares and only lots held over the merger. So:
* `Description Box 1a` is `VMWARE INC CLASS A`
* `DATE SOLD (Box 1c)` is `11/24/23`

For these lots I expect all of the dollar value fields to be `$0.00` except for `PROCEEDS (Box 1d)` and `GAIN(LOSS) AMOUNT`. If you've got values in any other column you'll need to understand why. Upvote [this tracking issue](https://github.com/hickeng/financial/issues/57) to flag the fact you're in this situation and the community can help figure out what it means.

For each of these lots you'll enter the values for some fields into the sheet. At the bottom of the 1099-B you will also have a `Total Reportable Amounts` section


## ESPP




## RSU

### eTrade 1099-B

## Income & Taxes

* 2022 1040
* 2023 W2
* Estimated Payments
* Deductions & Filing Status

## Sale of AVGO in 2023 post-merger



# Outputs

## Merger details

### 2023 Captial Gain & Cash Consideration

### Future Captial Gain


# Estimated Tax


# Custom Functions

## Export

## Optimizer