# CryptoTuner
Script to automatically find optimized and stable GPU overclock settings to mine Ethereum.

# What it does
This software does exactly what you would do manually to reach peak speeds/efficiency on your GPUs - but in a parallel, automatically yet accurate way.

## Features for automated GPU Overclocking & Power Limiting
* Thermal Throttling detection
* Automatic down-clocking on mining software crash, instability or invalid shares
* Three Optimization Modes: 
    * Efficiency: get the best Hash/Watt ratio
    * Speed: achieve the highest sense-making speed
    * Profitability: get the best profitability with your power costs
* Parallel Optimization of all GPUs at the same time

### Thermal Throttling Detection
If your GPUs are reducing their Hashrate due to high temps or too high overclocks, the tool will inform you and reduce the clocks accordingly.

### Finding maximum Memory OC
The software will start overclocking your memory until either the mining software crashes or your GPU created invalid shares. This will help in reaching the maximum possible speed.

### Finding minimum Core Clock
After finding the maximum possible memory clock, the software will start reducing the core clock until a significant decrease in speed is detected. This will help decreasing the power consumption and temperatures of your GPUs.

### Finding minimum Power Limits
After clocks are fine tuned, each GPUs power limit will be reduced to lower temperatures and increase efficiency (lower power costs). There are three modes to choose from:
* Mode 0: Maximum Efficiency (default): your GPU will probably not reach it's top hash rate, but it will be the most efficient (power/hash) you can achieve
* Mode 1: Maximum Speed (hybrid): Your GPU will run some kHashes below it's maximum speed but can achieve this with a lot less power than default (see "offset"-parameter)
* Mode 2: Maximum Profitability: Enter your power_cost and "daily dollars per MHash" and get the best settings for achieving the highest profitability

### Tuning all GPUs in parallel
This software tracks your GPUs state every second, creates statistics from that and automatically sets your GPUs to your preferred model. All GPUs are tuned at the same time, therefore it is fast and accurate in it's decision making without writing down hundreds of values, speeds and efficiencies manually.

## Limitations
- Windows 10/11 only
- T-Rex Miner only

## Requirements
The following requirements need to be met in order for the tool to work properly
- NVIDIA Driver installed (especially nvidia-smi)
- Up-to-date Windows 10
- executing script with Administrative Access
- close MSI Afterburner or any other Overclock Tool (if running)

## Usage
The tool can be run as-is. It will pick default values for tuning which might not be perfect - but will work. **It is required to run the executable or batch-script with admin privileges (see warning above!).**
```
cryptotuner.exe --mode 2 --devices 0 1 2 3 --steps 10 --shares 3 --datapoints 30 --offset 0.35 --core_uc -200 --mem_oc 500 --power_limit 160 --power_cost 0.36 --dollar_per_mhash 0.065
```

See below list for aditional parameters:
* --help <-h>: Shows a help message on the console with all possible arguments and options.
* --mode <-m>: Defines which optimization mode for power limit should be applied, "--mode 0" (Efficiency) "--mode 1" (Speed) "--mode 2" (Profitability)
* --devices <-d>: list of GPUs by id that should be tuned, seperated by a blank space e.g. "--devices 0 1 2 3"
* --steps <-s>: step size to in/decrease memory and core clocks per run e.g. "--steps 5" will increase or decrease clocks 5 Mhz at a time - lower values increase accuracy of result but take longer time to complete the overall process
* --shares <-x>: number of shares each GPU needs to generate before settings are validated e.g. "--shares 5". More shares increases stability but increases overall process time
* --datapoints <-e>: minimum number of datapoints which are required to compare results e.g. "--datapoints 50". Higher values mean more reliable results. Duration impact is minimal. Minimum value is 30.
* --offset <-o>: to compare speed results e.g. "--offset 0.35". If set too low, your efficiency will suffer. If set too high, the efficiency will be fine but your speed result will suffer, feel free to play with this but 0.35 is a good starting point.
* --core_uc <-c>: starting value of core underclock e.g. "--core_uc -200" will begin the core underclock with -200mhz. Separate values for multiple GPUs with a blank space e.g. "--core_uc -200 -100 -50"
* --mem_oc <-M>: starting value of memory overclock e.g. "--mem_oc 1000" will begin the memory overclock with +1000mhz. Separate values for multiple GPUs with a blank space e.g. "--mem_oc 1000 800 550"
* --mem_tweak <-t>: memory tweak parameter for compatible cards. Separate values for multiple GPUs with a blank space e.g. "--mem_tweak 1 0 3"
* --power_limit <-p>: starting value of power limit e.g. "--power_limit 240" will begin power limit reduction at 240 watts. Separate values for multiple GPUs with a blank space e.g. "--power_limit 240 230 250"
* --watt_steps <-w>: step size to in/decrease power limit per run e.g. "--watt_steps 5" will increase or decrease power limit 5 Watts at a time
* --power_cost <-C>: define how much your power costs $/kWh, needed to calculate profitability in mode 2
* --dollar_per_mhash <-D>: define the value of 1 MHash, needed to calculate profitability in mode 2 - you can find out via https://whattomine.com/
* --load_preset <-l>: load a preset from the GPU database that is fitting to your cards. If no settings could be found, your provided OC settings (if any) or default values for the OC will be applied (MEM +0 / Core +0/ PL 100% / Fan Temp: 60ºC)
* --skip_core : skip the core underlcock optimization process.
* --skip_mem : skip the memory overlock optimization process.
* --skip_power : skip the power limit optimization process.
* --verbose : adds more verbosity to the console interface (up to 3 levels). Logs will still have the full information.
* --keep_mining <-k>: once finished with the Tuning, this flag keeps the miners working until the user hits "Enter"
* --resume <-r>: constatly writes a file with the progress of the Tuning. If the computer were to crash or the tuning had to be stopped for whatever reason, if this flag is set and the "process.json" file is present, the tool will resume the Tuning process from where it was left at.
* --serial <-s>: flag for doing the optimization on a serialized way (instead of parallel) for the GPUs. Useful for when PSU has not enough power or when other GPUs are generating too much heat or interfering with eachothers optimization.

## Support
Bitcoin Talk Forum: https://bitcointalk.org/index.php?topic=5368267.0

## Contribution / Donation
By default, running the tool will mine some shares to my wallet address as a way to help me keep developing this tool.
If you want to pursue a more direct approach, feel free to use below crypto wallets.
#### Ethereum: 0xec64ad21a91fcd8d9bf1127dfe0fdba851c2eb01 (ONLY ERC20) ####
![Ethereum Wallet QR-Code](https://github.com/CryptoTuner/CryptoTuner/raw/main/wallets/ethereum-wallet.png)
#### Bitcoin: 1D3sK7NnTa483Wthkj829Uj4A8LyhreMob #### 
![Bitcoin Wallet QR-Code](https://github.com/CryptoTuner/CryptoTuner/raw/main/wallets/bitcoin-wallet.png)