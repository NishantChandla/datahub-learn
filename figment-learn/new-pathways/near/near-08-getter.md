Our Contract is on-chain, and we're going to learn how to fetch the message stored on the contract. 

{% hint style="working" %}
If you want to learn more about NEAR smart contracts, you can follow the tutorial [here](https://learn.figment.io/tutorials/write-and-deploy-a-smart-contract-on-near)
{% endhint %}

----------------------------------

# Challenge

{% hint style="tip" %}
In`pages/api/near/getter.ts`, implement the default function. You must replace any instances of `undefined` with working code to accomplish this.
{% endhint %}

**Take a few minutes to figure this out.**

```tsx
//...
  try {
    const { network, accountId  } = req.body;
    const config = configFromNetwork(network);
    const near = await connect(config);
    const account = await near.account(accountId);
    // Using viewFunction, try to call the contract 
    const response = undefined;
    return res.status(200).json(response)
  }
//...
```

**Need some help?** Check out this link!
* [Learn about `viewFunction`](https://near.github.io/near-api-js/classes/account.account-1.html#viewfunction)  

{% hint style="info" %}
You can [**join us on Discord**](https://discord.gg/fszyM7K), if you have questions or want help completing the tutorial.
{% endhint %}

Still not sure how to do this? No problem! The solution is below so you don't get stuck.

----------------------------------

# Solution

```tsx
// solution
//...
  try {
    const { network, accountId  } = req.body;
    const config = configFromNetwork(network);
    const near = await connect(config);
    const account = await near.account(accountId);
    const response = await account.viewFunction(
        accountId, 
        "get_greeting", 
        {account_id: accountId}
    );
    return res.status(200).json(response)
  }
//...
```

**What happened in the code above?**

* We're calling the `viewFunction` method of our account, passing to it:
  * The `contractId`, which is the same as our account name. This is because the contract has been deployed to our account!
  * The name of the method we want to call, here `get_greeting`
  * The name of the argument expected by `get_greeting`, which is `account_id`.
* Finally, we can send the `response` back to the client-side as JSON. 

----------------------------------

# Make sure it works

Once you have the code above saved, click the button and watch the magic happen:

![](../../../.gitbook/assets/pathways/near/near-getter.gif)

----------------------------------

# Conclusion
Now, time for the last challenge! Time to modify the state of the contract and thus the state of the blockchain. Let's go!
