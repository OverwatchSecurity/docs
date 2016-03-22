# Overwatch Usage

The Overwatch agent has a command line interface that allows you to perform basic administrative tasks. You should have the executable available as `overwatchd` in your `PATH`.

## Register agent through CLI

The agent can register itself without you accessing the Overwatch web interface.

### Register interactively

```bash
$ sudo overwatchd --register --name "Media Center Raspberry Pi"
```

This will prompt an interactive email/password input and register the device under the ownership of the authenticating user. The `--name` flag is optional and Overwatch will generate a name if none is specified.

### Register non-interactively

Alternatively, you can specify a `--token <token>` to skip the interactive prompt. This token is associated with your account and this step will register the device under your account directly. This is especially useful when installing the agent in bulk on multiple devices.

```bash
$ sudo overwatchd --register --name "Smoke detector" --token Xdj2kdlajk3dfjsk2j31hdlrgk3od12isdjiqk2m22i3jdfui
```

### Get registration token

You can get your registration token at any time with the `--get-token` flag. You will be required to provide login credentials.

```bash
$ overwatchd --get-token
```

### Regenerating identity file

You can recreate SSH identity keys at any point. If you do, you will need to register your device again, as it will appear to Overwatch as a completely new and unrelated device.

```bash
$ sudo overwatchd --generate-keys --override
```

## Starting the agent manually

The Overwatch agent is installed as a service on your device, as such, you'll be able to issue standard service commands to control its behavior.

### On Upstart systems
```bash
$ sudo service overwatchd start
$ sudo service overwatchd restart
$ sudo service overwatchd stop
```
