# Makefile to install arch-upgrade

# Installation directory
INSTALL_DIR = $(HOME)/.local/bin
SCRIPT = arch-upgrade
TARGET = $(INSTALL_DIR)/arch-upgrade

# Default rule
all: install

# Install the script
install: $(SCRIPT)
    @mkdir -p $(INSTALL_DIR)
    @install -m 755 $(SCRIPT) $(TARGET)
    @echo "Script installed to $(TARGET)"
    @# Check if $HOME/.local/bin is in the PATH in .bashrc
    @if ! grep -q '$(INSTALL_DIR)' $(HOME)/.bashrc; then \
        echo 'export PATH="$$PATH:$(INSTALL_DIR)"' >> $(HOME)/.bashrc; \
        echo "Added $(INSTALL_DIR) to PATH in $(HOME)/.bashrc"; \
        echo "Please run 'source ~/.bashrc' or restart your terminal to apply the changes."; \
    else \
        echo "$(INSTALL_DIR) is already in the PATH in $(HOME)/.bashrc"; \
    fi

# Uninstall (cleanup)
uninstall:
    @rm -f $(TARGET)
    @echo "Script uninstalled from $(TARGET)"
    @# Note: I don’t automatically remove the line from .bashrc to avoid mistakes

# Check installation
check:
    @echo "Checking installation..."
    @[ -f $(TARGET) ] && echo "Script installed at $(TARGET)" || echo "Script not found at $(TARGET)"
    @command -v arch-upgrade >/dev/null 2>&1 && echo "arch-upgrade is in the PATH" || echo "arch-upgrade is not in the PATH (run 'source ~/.bashrc')"

.PHONY: all install uninstall check
