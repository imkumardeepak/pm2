PM2 COMMANDS CHEAT SHEET WITH COMMENTS
--------------------------------------

# 1. INSTALLATION
npm install -g pm2             # Install PM2 globally

# 2. STARTING APPLICATIONS
pm2 start app.js                # Start app.js with PM2
pm2 start app.js --name my-app  # Start app.js with a custom name
pm2 start app.js -i max         # Start app in cluster mode using all CPU cores
pm2 start app.js --watch        # Restart app automatically when files change
pm2 start app.js --ignore-watch="node_modules logs"  # Ignore specific folders/files
pm2 start app.js --env production   # Start with production environment variables
pm2 start npm -- start          # Start an npm script using PM2
pm2 start ecosystem.config.js   # Start apps from ecosystem config file

# 3. LISTING & MONITORING
pm2 list                        # Show all running processes
pm2 status                      # Same as 'pm2 list'
pm2 monit                       # Real-time monitoring dashboard
pm2 show 0                      # Show details for process with ID 0
pm2 describe my-app              # Show details for process by name

# 4. STOPPING & RESTARTING
pm2 stop all                    # Stop all running apps
pm2 stop my-app                 # Stop a specific app by name
pm2 stop 0                      # Stop a specific app by ID
pm2 restart all                 # Restart all apps
pm2 restart my-app              # Restart a specific app
pm2 reload all                  # Zero-downtime reload (cluster mode)
pm2 reload my-app               # Reload specific app
pm2 gracefulReload all          # Gracefully reload all apps

# 5. DELETING & CLEARING
pm2 delete all                  # Remove all apps from PM2 process list
pm2 delete my-app               # Remove a specific app by name
pm2 delete 0                    # Remove a specific app by ID
pm2 flush                       # Clear all PM2 logs
pm2 reset all                   # Reset all process counters and stats

# 6. LOGS
pm2 logs                        # Show logs for all apps
pm2 logs my-app                 # Show logs for a specific app
pm2 logs --lines 100            # Show the last 100 log lines
pm2 logs --json                 # Show logs in JSON format
pm2 logs --timestamp            # Show logs with timestamps
pm2 error my-app                # Show only error logs for a specific app

# 7. STARTUP SCRIPTS (AUTO START ON SERVER REBOOT)
pm2 startup                     # Generate startup script for your OS
pm2 startup systemd             # Generate startup script for systemd
pm2 save                        # Save current process list so they restart on reboot
pm2 resurrect                   # Restore saved process list

# 8. CONFIGURATION WITH ECOSYSTEM FILE
pm2 ecosystem                   # Generate ecosystem.config.js template
pm2 start ecosystem.config.js   # Start apps from ecosystem file
pm2 restart ecosystem.config.js # Restart apps from ecosystem file

# 9. MISC / ADVANCED
pm2 update                      # Update PM2 daemon
pm2 updatePM2                   # Upgrade PM2 to latest version
pm2 reloadLogs                  # Reload logs without restarting apps
pm2 env my-app                  # Show environment variables for a specific app
pm2 set key value               # Set PM2 internal config key/value
pm2 unset key                   # Remove PM2 internal config key
pm2 sendSignal SIGUSR2 0        # Send a custom signal to process with ID 0

# QUICK DAILY WORKFLOW
pm2 start app.js --name my-app  # Start app with custom name
pm2 list                        # View running processes
pm2 logs my-app                 # Check logs for specific app
pm2 restart my-app              # Restart the app
pm2 save                        # Save current processes for restart after reboot

-----------------------------------------------------------------------------------

pm2 start node --name "new-app" -- ./node_modules/next/dist/bin/next start -p 9002
pm2 logs new-app
pm2 save
pm2 startup


