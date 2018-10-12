# Browser testing

## IE11
IE11 is available through a EBI's remote Windows session using the Microsoft Remote Desktop (available from the Managed Software Centre).

### Note
These steps will make your development server available to all machines within the EBI network.

### Steps
1. Change the development server's host to `0.0.0.0`. For example in a webpack config you could have:
```
devServer: {
  ...
  host: '0.0.0.0',
  port: 3909,
  ...
}
```
2. Determine your machine's IP address:
  - Wireless: `ipconfig getifaddr en0`
  - Ethernet: `ipconfig getifaddr en1`

3. Log in to a remote Windows session with Microsoft Remote Desktop.
4. Open IE11 and visit `http://{IP address from step 2}:{the port used by your development server}`
